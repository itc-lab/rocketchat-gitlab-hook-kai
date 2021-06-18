# rocketchat-gitlab-hook-kai
[rocketchat-gitlab-hook](https://github.com/malko/rocketchat-gitlab-hook)の`return`の`attachments`を`text`に載せるようにしたもの。

例えば、以下のような変更が行われています。

```javascript
			return {
				content: {
					username: `gitlab/${project.name}`,
					icon_url: USE_ROCKETCHAT_AVATAR ? null : avatar,
					attachments: [
						makeAttachment(user, `pushed new branch [${refParser(data.ref)}](${web_url}/commits/${refParser(data.ref)}) to [${project.name}](${web_url}), which is ${data.total_commits_count} commits ahead of master`)
					]
				}
			};
```
↓
```javascript
			return {
				content: {
					text: `*${user ? displayName(user.name) : ''
						}*\n\`pushed new branch [${refParser(
							data.ref
						)}](${web_url}/commits/${refParser(data.ref)}) to [${project.name
						}](${web_url}), which is ${data.total_commits_count
						} commits ahead of master\``,
					username: `gitlab/${project.name}`,
					icon_url: USE_ROCKETCHAT_AVATAR ? null : avatar,
					// attachments: [
					// 	makeAttachment(user, `pushed new branch [${refParser(data.ref)}](${web_url}/commits/${refParser(data.ref)}) to [${project.name}](${web_url}), which is ${data.total_commits_count} commits ahead of master`)
					// ]
				}
			};
```
