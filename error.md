Run # 设置Git配置以处理自动合并 / Set Git config for automatic merging
  # 设置Git配置以处理自动合并 / Set Git config for automatic merging
  git config pull.rebase true
  git config rebase.autoStash true
  
  # 尝试推送，如果失败则拉取并重试 / Try to push, if failed then pull and retry
  for i in {1..3}; do
    echo "推送尝试 $i / Push attempt $i"
    if git push origin main; then
      echo "推送成功 / Push successful"
      break
    else
      echo "推送失败，拉取最新变更... / Push failed, pulling latest changes..."
      git pull origin main --no-edit || true
      if [ $i -eq 3 ]; then
        echo "3次尝试后推送失败 / Failed to push after 3 attempts"
        exit 1
      fi
    fi
  done
  shell: /usr/bin/bash -e {0}
推送尝试 1 / Push attempt 1
remote: Permission to duangkuacha/daily-arxiv.git denied to github-actions[bot].
fatal: unable to access 'https://github.com/duangkuacha/daily-arxiv/': The requested URL returned error: 403
推送失败，拉取最新变更... / Push failed, pulling latest changes...
From https://github.com/duangkuacha/daily-arxiv
 * branch            main       -> FETCH_HEAD
Current branch main is up to date.
推送尝试 2 / Push attempt 2
remote: Permission to duangkuacha/daily-arxiv.git denied to github-actions[bot].
fatal: unable to access 'https://github.com/duangkuacha/daily-arxiv/': The requested URL returned error: 403
推送失败，拉取最新变更... / Push failed, pulling latest changes...
From https://github.com/duangkuacha/daily-arxiv
 * branch            main       -> FETCH_HEAD
Current branch main is up to date.
推送尝试 3 / Push attempt 3
remote: Permission to duangkuacha/daily-arxiv.git denied to github-actions[bot].
fatal: unable to access 'https://github.com/duangkuacha/daily-arxiv/': The requested URL returned error: 403
推送失败，拉取最新变更... / Push failed, pulling latest changes...
From https://github.com/duangkuacha/daily-arxiv
 * branch            main       -> FETCH_HEAD
Current branch main is up to date.
3次尝试后推送失败 / Failed to push after 3 attempts
Error: Process completed with exit code 1.