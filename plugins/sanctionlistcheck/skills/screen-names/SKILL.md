---
name: screen-names
description: Screen the names of people or companies against 10 official sanctions lists with the SanctionListCheck tools. Use it when the user asks to check names, a customer list, a supplier list or a file of names against sanctions lists such as OFAC SDN, the EU, the UK or the UN.
---

# Screen names against sanctions lists

The SanctionListCheck tools are `screen_names`, `get_record`, `list_sources` and `get_balance`.
A hit is a possible match for a person to review. A hit never shows that a person or company is on a list.

## 1. Collect the names

- From a chat message: take each name as the user wrote it.
- From a file: find every column that holds the name of a party, for example customer, supplier, director, beneficiary or contact. Screen each of these columns, not only the first one.
- Skip an empty cell. Report it as "not screened: empty". Never report an empty cell as a name with no hit.
- Add the context that the file gives: `country`, `dob` (date of birth, persons only) and `type` (`person` or `entity`). Do not guess a value that the file does not give.

## 2. Check the cost

- One screened name costs 1 credit. `get_balance` and `list_sources` cost nothing.
- Call `get_balance`. Tell the user the number of names and the balance.
- Ask the user before you screen more than 100 names, or more names than the balance.

## 3. Screen

- `screen_names` takes 1 to 100 names in one call. Split a longer list into calls of 100 names or fewer.
- Give each call an `idempotency_key`, for example the file name and the batch number. A retry with the same key within 24 hours returns the stored record and charges no credits.
- Keep the `record_id` of each call.

## 4. Show the result

- Show one table: the name as written, the file row (for a file), the listed name of the hit, the list, the score and the record ID.
- Sort the hits by score, highest first. A score of 0.9 or more is a strong name match. A score from 0.6 is a possible match.
- For a name without a hit, write: "No list entry reached a score of 0.6." When the user set a higher `threshold`, use that number.
- Give the data date of each list. The response of `screen_names` and `list_sources` holds it.
- Write once, under the table: "A hit is a possible match for a person to review."
- Do not write that a name is clear, safe, approved or sanctioned. The person who reviews the hits decides.

## 5. Later

- `get_record` with a record ID shows a screening again. It costs nothing.
- When the balance is too low, `screen_names` returns an error. Tell the user the balance. `get_balance` gives the link to the page for more credits.
