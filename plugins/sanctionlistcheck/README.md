# SanctionListCheck plugin for Claude

Screen names against 10 official sanctions lists, including OFAC SDN, the EU, the UK and the UN. Each hit is a possible match for a person to review.

SanctionListCheck screens the names of people and companies against 10 official sanctions lists: OFAC SDN, the US Consolidated Screening List, the EU consolidated list, the UK Sanctions List, the UN Security Council Consolidated List, and the national lists of France, Poland, Switzerland, Canada and Australia. We fetch each list from its official publisher every day.

Ask in plain words, for example: "Screen these names against the sanctions lists." Claude shows each hit with its score, its list and a record ID. The engine also finds other spellings and word orders. The matching uses no AI model.

A hit is a possible match for a person to review. Each screening is saved as a record: the names, the hits, the date of each list and the engine version. You can open a record again with its ID. The screened names in a record are kept for 90 days by default.

Sign in with your email address and a 6-digit code. A new email address gets 100 free credits. One screened name costs 1 credit. To open a record, list the sources or check your balance costs nothing.

## What the plugin adds

- The SanctionListCheck connector: the remote MCP server `https://sanctionlistcheck.com/mcp` with the tools `screen_names`, `get_record`, `list_sources` and `get_balance`.
- The skill `screen-names`: the steps to screen a list or a file of names, check the credit cost first, and show each hit for review.

## Install in Claude Code

```
/plugin marketplace add MiguelCasaresRobles/sanctionlistcheck-claude-plugin
/plugin install sanctionlistcheck@sanctionlistcheck
```

Then run `/mcp`, select `sanctionlistcheck` and sign in with your email address and the 6-digit code.

## Example prompts

- Screen these names against the sanctions lists: Vladimir Putin, Maria Ivanova. Give me the record ID and the lists with a hit.
- Which sanctions lists do you check, and what is the data date of each list?
- Fetch the record of my last screening and list the hits with a score of 0.95 or higher.

## Links

- Guide: https://sanctionlistcheck.com/mcp
- Privacy policy: https://sanctionlistcheck.com/privacy
- Terms: https://sanctionlistcheck.com/terms
- Support: support@sanctionlistcheck.com

## License

The MIT license covers the files in this repository. It does not give any right to use the SanctionListCheck name or logo.
