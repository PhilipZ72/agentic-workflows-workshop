---
# Trigger - when should this workflow run?
on:
  schedule: daily  # Fuzzy daily schedule (scattered execution time)
permissions:
  contents: read
  discussions: read
  issues: read
  pull-requests: read

network:
  allowed:
    - https://hacker-news.firebaseio.com

safe-outputs:
  create-discussion: null
  create-issue: null

---

## Instructions

When this workflow runs, the AI should:
Create a daily digest workflow for professional developers, referencing
relevant top Hacker News stories on technology that can be used today
by large companies. Every weekday, fetch the top 30 stories from the
Hacker News API (https://hacker-news.firebaseio.com/v0/topstories.json),
filter to stories with a score above 100 that are about software
engineering, cloud infrastructure, AI/ML, developer tooling, or
distributed systems. For each qualifying story include: the title, the
URL, the score, the number of comments, and a one-sentence summary of
why it is relevant to enterprise developers. Create a GitHub issue
titled "HN Digest – <date>" with the results formatted as a Markdown
table. The issue should be tagged with "HN Digest" and assigned to the
repository's maintainers. If there are no qualifying stories, create an issue stating "No relevant stories found for <date>" and tag it with "HN Digest". The issue should be created in a private repository to ensure that the digest is only accessible to the intended audience. The workflow should run every weekday at 9 AM UTC. The workflow should also include error handling to manage potential issues with the API or data processing, and it should log any errors encountered during execution for troubleshooting purposes. The workflow should be designed to be easily maintainable and extensible, allowing for future enhancements such as additional filtering criteria or integration with other platforms. The workflow should also include documentation on how to set it up and customize it for different use cases, such as changing the filtering criteria or the format of the digest. Additionally, the workflow should be optimized for performance, ensuring that it can fetch and process the data efficiently without hitting rate limits or causing timeouts. Finally, the workflow should be tested thoroughly to ensure that it works as expected and handles edge cases gracefully. The documentation should be included in the repository's README file, providing clear instructions on how to set up the workflow, customize it, and troubleshoot common issues. The workflow should also include comments in the code to explain the logic and make it easier for other developers to understand and modify as needed. Overall, the goal of this workflow is to provide a valuable resource for enterprise developers by delivering a curated selection of relevant Hacker News stories in an easily digestible format on a daily basis.