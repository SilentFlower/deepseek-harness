# Bootstrap Task: Fill Project Development Guidelines

**You (the AI) are running this task. The developer does not read this file.**

The developer just ran `trellis init` on this project for the first time.
`.trellis/` now exists with empty spec scaffolding, and this bootstrap task
exists under `.trellis/tasks/`. When they want to work on it, they should start
this task from a session that provides Trellis session identity.

**Your job**: help them populate `.trellis/spec/` with the team's real
coding conventions. Every future AI session — this project's
`trellis-implement` and `trellis-check` sub-agents — auto-loads spec files
listed in per-task jsonl manifests. Empty spec = sub-agents write generic
code. Real spec = sub-agents match the team's actual patterns.

Don't dump instructions. Open with a short greeting, figure out if the repo
has any existing convention docs (CLAUDE.md, .cursorrules, etc.), and drive
the rest conversationally.

---

## Status (update the checkboxes as you complete each item)

- [ ] Fill guidelines for @deepseek-ai/cordis
- [ ] Fill guidelines for @deepseek-ai/cosmokit
- [ ] Fill guidelines for @deepseek-ai/cordis-plugin-group
- [ ] Fill guidelines for @deepseek-ai/cordis-plugin-hmr
- [ ] Fill guidelines for @deepseek-ai/cordis-plugin-include
- [ ] Fill guidelines for @deepseek-ai/cordis-plugin-loader
- [ ] Fill guidelines for @deepseek-ai/cordis-plugin-logger-console
- [ ] Fill guidelines for @deepseek-ai/schemastery
- [ ] Fill guidelines for @deepseek-ai/cordis-plugin-timer
- [ ] Fill guidelines for @deepseek-ai/dsh-acp
- [ ] Fill guidelines for @deepseek-ai/dsh-api-account-controller
- [ ] Fill guidelines for @deepseek-ai/dsh-api-gateway
- [ ] Fill guidelines for @deepseek-ai/dsh-api-job-controller
- [ ] Fill guidelines for @deepseek-ai/dsh-api-remote-access
- [ ] Fill guidelines for @deepseek-ai/dsh-api-remotes
- [ ] Fill guidelines for @deepseek-ai/dsh-api-session-controller
- [ ] Fill guidelines for @deepseek-ai/dsh-api-settings-controller
- [ ] Fill guidelines for @deepseek-ai/dsh-api-terminal-controller
- [ ] Fill guidelines for @deepseek-ai/dsh-api-workspace-controller
- [ ] Fill guidelines for @deepseek-ai/dsh-api-workspace-files
- [ ] Fill guidelines for @deepseek-ai/dsh-attachment
- [ ] Fill guidelines for @deepseek-ai/dsh-attachment-local
- [ ] Fill guidelines for @deepseek-ai/dsh-app-boot
- [ ] Fill guidelines for @deepseek-ai/dsh-cmdline
- [ ] Fill guidelines for @deepseek-ai/dsh-config-editor
- [ ] Fill guidelines for @deepseek-ai/dsh-hmr
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-manager
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-market
- [ ] Fill guidelines for @deepseek-ai/dsh-browser-use
- [ ] Fill guidelines for @deepseek-ai/dsh-acp-app
- [ ] Fill guidelines for @deepseek-ai/dsh-base
- [ ] Fill guidelines for @deepseek-ai/dsh-headless
- [ ] Fill guidelines for @deepseek-ai/dsh-sdk-app
- [ ] Fill guidelines for @deepseek-ai/dsh-sdk-minimal
- [ ] Fill guidelines for @deepseek-ai/dsh-web-app
- [ ] Fill guidelines for @deepseek-ai/dsh-client-connection
- [ ] Fill guidelines for @deepseek-ai/dsh-client-file-upload
- [ ] Fill guidelines for @deepseek-ai/dsh-client-hmr
- [ ] Fill guidelines for @deepseek-ai/dsh-client-locale
- [ ] Fill guidelines for @deepseek-ai/dsh-client-modules
- [ ] Fill guidelines for @deepseek-ai/dsh-client-product-analytics
- [ ] Fill guidelines for @deepseek-ai/dsh-client-resources
- [ ] Fill guidelines for @deepseek-ai/dsh-client-shortcuts
- [ ] Fill guidelines for @deepseek-ai/dsh-client-store
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-agent-preset
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-agent-team
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-approval
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-attachment
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-brand-official
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-chat
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-commands
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-context-menu
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-conversation
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-deliverables
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-directory-picker-browse
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-directory-picker-native
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-dockkit
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-entry-customization
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-file-actions
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-file-drag
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-goal
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-input-trigger
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-jobs
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-layout
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-message-feedback
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-model-selection
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-open-in-app
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-permission-presets
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-plan
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-plugin-manager
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-plugin-market
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-primitives
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-reference
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-renderer
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-schedule
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-secret-mask
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-session
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-account
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-agent-loop
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-general
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-models
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-plugin-inventory
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-plugins
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-session-log
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-shell
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-subagent
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-settings-web-search
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-shortcuts
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-sidebar
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-sidebar-browser
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-sidebar-documentpreview
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-sidebar-files
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-sidebar-right
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-sidebar-terminal
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-skill
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-slots
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-subagent
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-theme
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-tool
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-trajectory
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-user-questions
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-workflow-run
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-workspace
- [ ] Fill guidelines for @deepseek-ai/dsh-client-web
- [ ] Fill guidelines for @deepseek-ai/dsh-command-compact
- [ ] Fill guidelines for @deepseek-ai/dsh-compaction
- [ ] Fill guidelines for @deepseek-ai/dsh-compaction-basic
- [ ] Fill guidelines for @deepseek-ai/dsh-compaction-image-offload
- [ ] Fill guidelines for @deepseek-ai/dsh-compaction-tool-result-pruner
- [ ] Fill guidelines for @deepseek-ai/dsh-computer-use
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-instructions
- [ ] Fill guidelines for @deepseek-ai/dsh-file-reference
- [ ] Fill guidelines for @deepseek-ai/dsh-file-reference-local
- [ ] Fill guidelines for @deepseek-ai/dsh-harness-dev-context
- [ ] Fill guidelines for @deepseek-ai/dsh-session-reference
- [ ] Fill guidelines for @deepseek-ai/dsh-time-context
- [ ] Fill guidelines for @deepseek-ai/dsh-tmux-context
- [ ] Fill guidelines for @deepseek-ai/dsh-agent
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-default-model
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-loop
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-tool-presentation
- [ ] Fill guidelines for @deepseek-ai/dsh-scope
- [ ] Fill guidelines for @deepseek-ai/dsh-session
- [ ] Fill guidelines for @deepseek-ai/dsh-system-prompt
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-executor-native
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-executor-ptc
- [ ] Fill guidelines for @deepseek-ai/dsh-tools
- [ ] Fill guidelines for @deepseek-ai/dsh-authorization
- [ ] Fill guidelines for @deepseek-ai/dsh-credentials
- [ ] Fill guidelines for @deepseek-ai/dsh-credentials-local
- [ ] Fill guidelines for @deepseek-ai/dsh-deepseek-account
- [ ] Fill guidelines for @deepseek-ai/dsh-deepseek-account-platform
- [ ] Fill guidelines for @deepseek-ai/dsh-deliverable-file-references
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-present
- [ ] Fill guidelines for @deepseek-ai/dsh-workspace-changes
- [ ] Fill guidelines for @deepseek-ai/dsh-office-to-pdf
- [ ] Fill guidelines for @deepseek-ai/dsh-action-cards
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-api-speech-to-text
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-auto-review
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-badge-skill-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-browser-use-chrome-devtools-mcp
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-browser-use-playwright-mcp
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-browser-use-runtime
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-browser-use-stagehand-native
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-claude-code-mods
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-action-cards
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-client-ui-claude-code-mods
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-client-ui-cot-translation
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-creation-recommendations
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-client-ui-forge
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-plugin-recommendations
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-client-ui-stats
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-client-ui-voice-input
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-computer-use-cua-driver-mcp
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-computer-use-cua-driver-native
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-cot-translation-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-creation-recommendations
- [ ] Fill guidelines for @deepseek-ai/dsh-cua
- [ ] Fill guidelines for @deepseek-ai/dsh-cua-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-cua-macos
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-forge
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-forge-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-forge-github
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-forge-session
- [ ] Fill guidelines for @deepseek-ai/dsh-hook-protocol
- [ ] Fill guidelines for @deepseek-ai/dsh-hooks-claude-code
- [ ] Fill guidelines for @deepseek-ai/dsh-hooks-codex
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-inspector
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-inspector-profile
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-liveshare
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-liveshare-protocol
- [ ] Fill guidelines for @deepseek-ai/dsh-personalized-recommendations
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-plugin-market-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-recommendations
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-ptc-runtime-python
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-ralph-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-session-inspector
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-session-search
- [ ] Fill guidelines for @deepseek-ai/dsh-session-title-all-prompts-llm
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-session-titles-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-skill-badge
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-speech-to-text
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-speech-to-text-sensevoice
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-subagent-oar
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-terminal-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-ralph
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-session-query
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-tool-subagent-oar
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-terminal
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-tool-worktree
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-translator
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-voice-input-bundle
- [ ] Fill guidelines for @deepseek-ai/dsh-webhook
- [ ] Fill guidelines for @deepseek-ai/dsh-webhook-github
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-webworker-packer
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-webworker-runtime
- [ ] Fill guidelines for @deepseek-ai/dsh-experimental-worktree
- [ ] Fill guidelines for @deepseek-ai/dsh-cordis-client-runner
- [ ] Fill guidelines for @deepseek-ai/dsh-cordis-host-runner
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-cordis
- [ ] Fill guidelines for @deepseek-ai/dsh-client-ui-cordis
- [ ] Fill guidelines for @deepseek-ai/dsh-command-feedback
- [ ] Fill guidelines for @deepseek-ai/dsh-message-feedback
- [ ] Fill guidelines for @deepseek-ai/dsh-fs
- [ ] Fill guidelines for @deepseek-ai/dsh-fs-local
- [ ] Fill guidelines for @deepseek-ai/dsh-fs-observation-policy
- [ ] Fill guidelines for @deepseek-ai/dsh-fs-patch
- [ ] Fill guidelines for @deepseek-ai/dsh-fs-sandbox
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-fs
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-fs-search
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-str-replace-editor
- [ ] Fill guidelines for @deepseek-ai/dsh-command-goal
- [ ] Fill guidelines for @deepseek-ai/dsh-goal
- [ ] Fill guidelines for @deepseek-ai/dsh-goal-round-driver
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-goal
- [ ] Fill guidelines for @deepseek-ai/dsh-repeat-tool-reminder
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-call-timeout-policy
- [ ] Fill guidelines for @deepseek-ai/dsh-host-directory-picker
- [ ] Fill guidelines for @deepseek-ai/dsh-host-directory-picker-auto
- [ ] Fill guidelines for @deepseek-ai/dsh-host-directory-picker-browse
- [ ] Fill guidelines for @deepseek-ai/dsh-host-directory-picker-native
- [ ] Fill guidelines for @deepseek-ai/dsh-host-frontend-static
- [ ] Fill guidelines for @deepseek-ai/dsh-host-open-in-app
- [ ] Fill guidelines for @deepseek-ai/dsh-host-plugin-inventory
- [ ] Fill guidelines for @deepseek-ai/dsh-host-product-telemetry-otel
- [ ] Fill guidelines for @deepseek-ai/dsh-host-webserver
- [ ] Fill guidelines for @deepseek-ai/dsh-anonymous-user-id
- [ ] Fill guidelines for @deepseek-ai/dsh-commands
- [ ] Fill guidelines for @deepseek-ai/dsh-permission-presets
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-ask-user
- [ ] Fill guidelines for @deepseek-ai/dsh-user-approval
- [ ] Fill guidelines for @deepseek-ai/dsh-user-questions
- [ ] Fill guidelines for @deepseek-ai/dsh-jobs
- [ ] Fill guidelines for @deepseek-ai/dsh-jobs-local
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-jobs
- [ ] Fill guidelines for @deepseek-ai/dsh-deepseek-llm-api-extensions
- [ ] Fill guidelines for @deepseek-ai/dsh-llm
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-deepseek
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-deepseek-account
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-deepseek-api-key
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-pi-ai
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-retry
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-package-inventory-deepseek
- [ ] Fill guidelines for @deepseek-ai/dsh-token-meter
- [ ] Fill guidelines for @deepseek-ai/dsh-lsp
- [ ] Fill guidelines for @deepseek-ai/dsh-lsp-stdio
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-lsp
- [ ] Fill guidelines for @deepseek-ai/dsh-mcp-client
- [ ] Fill guidelines for @deepseek-ai/dsh-mcp-manager
- [ ] Fill guidelines for @deepseek-ai/dsh-mcp-resources
- [ ] Fill guidelines for @deepseek-ai/dsh-plan-mode
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-preset
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-preset-registry
- [ ] Fill guidelines for @deepseek-ai/dsh-persona
- [ ] Fill guidelines for @deepseek-ai/dsh-ptc-runtime
- [ ] Fill guidelines for @deepseek-ai/dsh-ptc-runtime-node
- [ ] Fill guidelines for @deepseek-ai/dsh-sandbox
- [ ] Fill guidelines for @deepseek-ai/dsh-sandbox-local
- [ ] Fill guidelines for @deepseek-ai/dsh-sandbox-policy
- [ ] Fill guidelines for @deepseek-ai/dsh-sandbox-windows-acl
- [ ] Fill guidelines for @deepseek-ai/dsh-schedule
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-schedule
- [ ] Fill guidelines for @deepseek-ai/dsh-sdk-client
- [ ] Fill guidelines for @deepseek-ai/dsh-sdk-protocol
- [ ] Fill guidelines for @deepseek-ai/dsh-sdk-jsonrpc-server
- [ ] Fill guidelines for @deepseek-ai/dsh-message-quotes
- [ ] Fill guidelines for @deepseek-ai/dsh-session-checkpoint-policy
- [ ] Fill guidelines for @deepseek-ai/dsh-session-format
- [ ] Fill guidelines for @deepseek-ai/dsh-session-format-catalog
- [ ] Fill guidelines for @deepseek-ai/dsh-session-format-v0-to-v1
- [ ] Fill guidelines for @deepseek-ai/dsh-session-format-v1-to-v2
- [ ] Fill guidelines for @deepseek-ai/dsh-session-format-v2-to-v3
- [ ] Fill guidelines for @deepseek-ai/dsh-session-format-v3-to-v4
- [ ] Fill guidelines for @deepseek-ai/dsh-session-log-deepseek
- [ ] Fill guidelines for @deepseek-ai/dsh-session-persistence
- [ ] Fill guidelines for @deepseek-ai/dsh-session-persistence-jsonl
- [ ] Fill guidelines for @deepseek-ai/dsh-session-projection
- [ ] Fill guidelines for @deepseek-ai/dsh-session-projection-cache
- [ ] Fill guidelines for @deepseek-ai/dsh-session-stats
- [ ] Fill guidelines for @deepseek-ai/dsh-session-telemetry
- [ ] Fill guidelines for @deepseek-ai/dsh-session-telemetry-otel
- [ ] Fill guidelines for @deepseek-ai/dsh-session-title
- [ ] Fill guidelines for @deepseek-ai/dsh-session-title-first-prompt-llm
- [ ] Fill guidelines for @deepseek-ai/dsh-session-title-llm
- [ ] Fill guidelines for @deepseek-ai/dsh-session-turn-outline
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-working-directory
- [ ] Fill guidelines for @deepseek-ai/dsh-working-directory
- [ ] Fill guidelines for @deepseek-ai/dsh-session-log-export
- [ ] Fill guidelines for @deepseek-ai/dsh-session-query
- [ ] Fill guidelines for @deepseek-ai/dsh-session-query-sqlite
- [ ] Fill guidelines for @deepseek-ai/dsh-settings
- [ ] Fill guidelines for @deepseek-ai/dsh-bash-local
- [ ] Fill guidelines for @deepseek-ai/dsh-bash-sandbox
- [ ] Fill guidelines for @deepseek-ai/dsh-pwsh-local
- [ ] Fill guidelines for @deepseek-ai/dsh-pwsh-sandbox
- [ ] Fill guidelines for @deepseek-ai/dsh-shell
- [ ] Fill guidelines for @deepseek-ai/dsh-shell-env
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-bash
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-bash-persistent
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-pwsh
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-pwsh-persistent
- [ ] Fill guidelines for @deepseek-ai/dsh-skill
- [ ] Fill guidelines for @deepseek-ai/dsh-skill-filesystem
- [ ] Fill guidelines for @deepseek-ai/dsh-skill-office
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-skill
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-workspace-dependencies
- [ ] Fill guidelines for @deepseek-ai/dsh-spill
- [ ] Fill guidelines for @deepseek-ai/dsh-spill-local
- [ ] Fill guidelines for @deepseek-ai/dsh-spill-policy
- [ ] Fill guidelines for @deepseek-ai/dsh-fs-ssh
- [ ] Fill guidelines for @deepseek-ai/dsh-sandbox-ssh
- [ ] Fill guidelines for @deepseek-ai/dsh-ssh
- [ ] Fill guidelines for @deepseek-ai/dsh-ssh-helper-runtime
- [ ] Fill guidelines for @deepseek-ai/dsh-subprocess-ssh
- [ ] Fill guidelines for @deepseek-ai/dsh-storage
- [ ] Fill guidelines for @deepseek-ai/dsh-storage-domain
- [ ] Fill guidelines for @deepseek-ai/dsh-storage-json
- [ ] Fill guidelines for @deepseek-ai/dsh-storage-sqlite
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent-acp
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent-claude-code
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent-codex
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent-dsh-sdk
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent-fork-in-process
- [ ] Fill guidelines for @deepseek-ai/dsh-subagent-spawn-in-process
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-subagent
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-subagent-control
- [ ] Fill guidelines for @deepseek-ai/dsh-subprocess
- [ ] Fill guidelines for @deepseek-ai/dsh-subprocess-local
- [ ] Fill guidelines for @deepseek-ai/dsh-win32-process
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-team
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-agent-team
- [ ] Fill guidelines for @deepseek-ai/dsh-otel
- [ ] Fill guidelines for @deepseek-ai/dsh-terminal
- [ ] Fill guidelines for @deepseek-ai/dsh-terminal-bash
- [ ] Fill guidelines for @deepseek-ai/dsh-agent-loop-testkit
- [ ] Fill guidelines for @deepseek-ai/dsh-client-test-runtime
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-mock-server
- [ ] Fill guidelines for @deepseek-ai/dsh-llm-replay
- [ ] Fill guidelines for @deepseek-ai/dsh-loader-smoke
- [ ] Fill guidelines for @deepseek-ai/dsh-remote-mock
- [ ] Fill guidelines for @deepseek-ai/dsh-session-snapshot
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-testkit
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-todo
- [ ] Fill guidelines for @deepseek-ai/dsh-typert-generator
- [ ] Fill guidelines for @deepseek-ai/dsh-typert-loader
- [ ] Fill guidelines for @deepseek-ai/dsh-typert-protocol
- [ ] Fill guidelines for @deepseek-ai/dsh-typert-registry
- [ ] Fill guidelines for @deepseek-ai/dsh-atomic-write
- [ ] Fill guidelines for @deepseek-ai/dsh-brand
- [ ] Fill guidelines for @deepseek-ai/dsh-chunked-list
- [ ] Fill guidelines for @deepseek-ai/dsh-util-code-language
- [ ] Fill guidelines for @deepseek-ai/dsh-util-crypto
- [ ] Fill guidelines for @deepseek-ai/dsh-deque
- [ ] Fill guidelines for @deepseek-ai/dsh-util-file-drag
- [ ] Fill guidelines for @deepseek-ai/dsh-home-paths
- [ ] Fill guidelines for @deepseek-ai/dsh-http-proxy
- [ ] Fill guidelines for @deepseek-ai/dsh-launch-environment
- [ ] Fill guidelines for @deepseek-ai/dsh-lazy-require
- [ ] Fill guidelines for @deepseek-ai/dsh-native-command
- [ ] Fill guidelines for @deepseek-ai/dsh-official-bundles
- [ ] Fill guidelines for @deepseek-ai/dsh-output-retention
- [ ] Fill guidelines for @deepseek-ai/dsh-package-manifest
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-detail
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-market-index
- [ ] Fill guidelines for @deepseek-ai/dsh-util-time
- [ ] Fill guidelines for @deepseek-ai/dsh-timeout
- [ ] Fill guidelines for @deepseek-ai/dsh-util-values
- [ ] Fill guidelines for @deepseek-ai/dsh-util-workspace-path
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-web
- [ ] Fill guidelines for @deepseek-ai/dsh-web
- [ ] Fill guidelines for @deepseek-ai/dsh-web-deepseek-api
- [ ] Fill guidelines for @deepseek-ai/dsh-web-fetch-http
- [ ] Fill guidelines for @deepseek-ai/dsh-web-search-deepseek
- [ ] Fill guidelines for @deepseek-ai/dsh-tool-workflow
- [ ] Fill guidelines for @deepseek-ai/dsh-workflow
- [ ] Fill guidelines for @deepseek-ai/dsh-workflow-ptc
- [ ] Fill guidelines for @deepseek-ai/dsh-workspace
- [ ] Fill guidelines for @deepseek-ai/node-addon-system-workspace
- [ ] Fill guidelines for @deepseek-ai/node-addon-system-darwin-arm64
- [ ] Fill guidelines for @deepseek-ai/node-addon-system-darwin-x64
- [ ] Fill guidelines for @deepseek-ai/node-addon-system
- [ ] Fill guidelines for @deepseek-ai/node-addon-system-linux-arm64
- [ ] Fill guidelines for @deepseek-ai/node-addon-system-linux-x64
- [ ] Fill guidelines for @deepseek-ai/dsh
- [ ] Fill guidelines for @deepseek-ai/dsh-desktop
- [ ] Fill guidelines for @deepseek-ai/dsh-desktop-host
- [ ] Fill guidelines for @deepseek-ai/dsh-plugin-market-generator
- [ ] Fill guidelines for @deepseek-ai/dsh-web-frontend
- [ ] Fill guidelines for @deepseek-ai/dsh-benchmarks
- [ ] Fill guidelines for @deepseek-ai/website
- [ ] Fill guidelines for dsh-python-runtime-closure
- [ ] Add code examples

---

## Spec files to populate

### Package: @deepseek-ai/cordis (`spec/cordis/`)

- Backend guidelines: `.trellis/spec/cordis/backend/`

- Frontend guidelines: `.trellis/spec/cordis/frontend/`

### Package: @deepseek-ai/cosmokit (`spec/cosmokit/`)

- Backend guidelines: `.trellis/spec/cosmokit/backend/`

- Frontend guidelines: `.trellis/spec/cosmokit/frontend/`

### Package: @deepseek-ai/cordis-plugin-group (`spec/cordis-plugin-group/`)

- Backend guidelines: `.trellis/spec/cordis-plugin-group/backend/`

- Frontend guidelines: `.trellis/spec/cordis-plugin-group/frontend/`

### Package: @deepseek-ai/cordis-plugin-hmr (`spec/cordis-plugin-hmr/`)

- Backend guidelines: `.trellis/spec/cordis-plugin-hmr/backend/`

- Frontend guidelines: `.trellis/spec/cordis-plugin-hmr/frontend/`

### Package: @deepseek-ai/cordis-plugin-include (`spec/cordis-plugin-include/`)

- Backend guidelines: `.trellis/spec/cordis-plugin-include/backend/`

- Frontend guidelines: `.trellis/spec/cordis-plugin-include/frontend/`

### Package: @deepseek-ai/cordis-plugin-loader (`spec/cordis-plugin-loader/`)

- Backend guidelines: `.trellis/spec/cordis-plugin-loader/backend/`

- Frontend guidelines: `.trellis/spec/cordis-plugin-loader/frontend/`

### Package: @deepseek-ai/cordis-plugin-logger-console (`spec/cordis-plugin-logger-console/`)

- Backend guidelines: `.trellis/spec/cordis-plugin-logger-console/backend/`

- Frontend guidelines: `.trellis/spec/cordis-plugin-logger-console/frontend/`

### Package: @deepseek-ai/schemastery (`spec/schemastery/`)

- Backend guidelines: `.trellis/spec/schemastery/backend/`

- Frontend guidelines: `.trellis/spec/schemastery/frontend/`

### Package: @deepseek-ai/cordis-plugin-timer (`spec/cordis-plugin-timer/`)

- Backend guidelines: `.trellis/spec/cordis-plugin-timer/backend/`

- Frontend guidelines: `.trellis/spec/cordis-plugin-timer/frontend/`

### Package: @deepseek-ai/dsh-acp (`spec/dsh-acp/`)

- Backend guidelines: `.trellis/spec/dsh-acp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-acp/frontend/`

### Package: @deepseek-ai/dsh-api-account-controller (`spec/dsh-api-account-controller/`)

- Backend guidelines: `.trellis/spec/dsh-api-account-controller/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-account-controller/frontend/`

### Package: @deepseek-ai/dsh-api-gateway (`spec/dsh-api-gateway/`)

- Backend guidelines: `.trellis/spec/dsh-api-gateway/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-gateway/frontend/`

### Package: @deepseek-ai/dsh-api-job-controller (`spec/dsh-api-job-controller/`)

- Backend guidelines: `.trellis/spec/dsh-api-job-controller/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-job-controller/frontend/`

### Package: @deepseek-ai/dsh-api-remote-access (`spec/dsh-api-remote-access/`)

- Backend guidelines: `.trellis/spec/dsh-api-remote-access/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-remote-access/frontend/`

### Package: @deepseek-ai/dsh-api-remotes (`spec/dsh-api-remotes/`)

- Backend guidelines: `.trellis/spec/dsh-api-remotes/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-remotes/frontend/`

### Package: @deepseek-ai/dsh-api-session-controller (`spec/dsh-api-session-controller/`)

- Backend guidelines: `.trellis/spec/dsh-api-session-controller/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-session-controller/frontend/`

### Package: @deepseek-ai/dsh-api-settings-controller (`spec/dsh-api-settings-controller/`)

- Backend guidelines: `.trellis/spec/dsh-api-settings-controller/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-settings-controller/frontend/`

### Package: @deepseek-ai/dsh-api-terminal-controller (`spec/dsh-api-terminal-controller/`)

- Backend guidelines: `.trellis/spec/dsh-api-terminal-controller/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-terminal-controller/frontend/`

### Package: @deepseek-ai/dsh-api-workspace-controller (`spec/dsh-api-workspace-controller/`)

- Backend guidelines: `.trellis/spec/dsh-api-workspace-controller/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-workspace-controller/frontend/`

### Package: @deepseek-ai/dsh-api-workspace-files (`spec/dsh-api-workspace-files/`)

- Backend guidelines: `.trellis/spec/dsh-api-workspace-files/backend/`

- Frontend guidelines: `.trellis/spec/dsh-api-workspace-files/frontend/`

### Package: @deepseek-ai/dsh-attachment (`spec/dsh-attachment/`)

- Backend guidelines: `.trellis/spec/dsh-attachment/backend/`

- Frontend guidelines: `.trellis/spec/dsh-attachment/frontend/`

### Package: @deepseek-ai/dsh-attachment-local (`spec/dsh-attachment-local/`)

- Backend guidelines: `.trellis/spec/dsh-attachment-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-attachment-local/frontend/`

### Package: @deepseek-ai/dsh-app-boot (`spec/dsh-app-boot/`)

- Backend guidelines: `.trellis/spec/dsh-app-boot/backend/`

- Frontend guidelines: `.trellis/spec/dsh-app-boot/frontend/`

### Package: @deepseek-ai/dsh-cmdline (`spec/dsh-cmdline/`)

- Backend guidelines: `.trellis/spec/dsh-cmdline/backend/`

- Frontend guidelines: `.trellis/spec/dsh-cmdline/frontend/`

### Package: @deepseek-ai/dsh-config-editor (`spec/dsh-config-editor/`)

- Backend guidelines: `.trellis/spec/dsh-config-editor/backend/`

- Frontend guidelines: `.trellis/spec/dsh-config-editor/frontend/`

### Package: @deepseek-ai/dsh-hmr (`spec/dsh-hmr/`)

- Backend guidelines: `.trellis/spec/dsh-hmr/backend/`

- Frontend guidelines: `.trellis/spec/dsh-hmr/frontend/`

### Package: @deepseek-ai/dsh-plugin-manager (`spec/dsh-plugin-manager/`)

- Backend guidelines: `.trellis/spec/dsh-plugin-manager/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plugin-manager/frontend/`

### Package: @deepseek-ai/dsh-plugin-market (`spec/dsh-plugin-market/`)

- Backend guidelines: `.trellis/spec/dsh-plugin-market/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plugin-market/frontend/`

### Package: @deepseek-ai/dsh-browser-use (`spec/dsh-browser-use/`)

- Backend guidelines: `.trellis/spec/dsh-browser-use/backend/`

- Frontend guidelines: `.trellis/spec/dsh-browser-use/frontend/`

### Package: @deepseek-ai/dsh-acp-app (`spec/dsh-acp-app/`)

- Backend guidelines: `.trellis/spec/dsh-acp-app/backend/`

- Frontend guidelines: `.trellis/spec/dsh-acp-app/frontend/`

### Package: @deepseek-ai/dsh-base (`spec/dsh-base/`)

- Backend guidelines: `.trellis/spec/dsh-base/backend/`

- Frontend guidelines: `.trellis/spec/dsh-base/frontend/`

### Package: @deepseek-ai/dsh-headless (`spec/dsh-headless/`)

- Backend guidelines: `.trellis/spec/dsh-headless/backend/`

- Frontend guidelines: `.trellis/spec/dsh-headless/frontend/`

### Package: @deepseek-ai/dsh-sdk-app (`spec/dsh-sdk-app/`)

- Backend guidelines: `.trellis/spec/dsh-sdk-app/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sdk-app/frontend/`

### Package: @deepseek-ai/dsh-sdk-minimal (`spec/dsh-sdk-minimal/`)

- Backend guidelines: `.trellis/spec/dsh-sdk-minimal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sdk-minimal/frontend/`

### Package: @deepseek-ai/dsh-web-app (`spec/dsh-web-app/`)

- Backend guidelines: `.trellis/spec/dsh-web-app/backend/`

- Frontend guidelines: `.trellis/spec/dsh-web-app/frontend/`

### Package: @deepseek-ai/dsh-client-connection (`spec/dsh-client-connection/`)

- Backend guidelines: `.trellis/spec/dsh-client-connection/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-connection/frontend/`

### Package: @deepseek-ai/dsh-client-file-upload (`spec/dsh-client-file-upload/`)

- Backend guidelines: `.trellis/spec/dsh-client-file-upload/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-file-upload/frontend/`

### Package: @deepseek-ai/dsh-client-hmr (`spec/dsh-client-hmr/`)

- Backend guidelines: `.trellis/spec/dsh-client-hmr/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-hmr/frontend/`

### Package: @deepseek-ai/dsh-client-locale (`spec/dsh-client-locale/`)

- Backend guidelines: `.trellis/spec/dsh-client-locale/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-locale/frontend/`

### Package: @deepseek-ai/dsh-client-modules (`spec/dsh-client-modules/`)

- Backend guidelines: `.trellis/spec/dsh-client-modules/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-modules/frontend/`

### Package: @deepseek-ai/dsh-client-product-analytics (`spec/dsh-client-product-analytics/`)

- Backend guidelines: `.trellis/spec/dsh-client-product-analytics/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-product-analytics/frontend/`

### Package: @deepseek-ai/dsh-client-resources (`spec/dsh-client-resources/`)

- Backend guidelines: `.trellis/spec/dsh-client-resources/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-resources/frontend/`

### Package: @deepseek-ai/dsh-client-shortcuts (`spec/dsh-client-shortcuts/`)

- Backend guidelines: `.trellis/spec/dsh-client-shortcuts/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-shortcuts/frontend/`

### Package: @deepseek-ai/dsh-client-store (`spec/dsh-client-store/`)

- Backend guidelines: `.trellis/spec/dsh-client-store/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-store/frontend/`

### Package: @deepseek-ai/dsh-client-ui-agent-preset (`spec/dsh-client-ui-agent-preset/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-agent-preset/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-agent-preset/frontend/`

### Package: @deepseek-ai/dsh-client-ui-agent-team (`spec/dsh-client-ui-agent-team/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-agent-team/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-agent-team/frontend/`

### Package: @deepseek-ai/dsh-client-ui-approval (`spec/dsh-client-ui-approval/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-approval/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-approval/frontend/`

### Package: @deepseek-ai/dsh-client-ui-attachment (`spec/dsh-client-ui-attachment/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-attachment/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-attachment/frontend/`

### Package: @deepseek-ai/dsh-client-ui-brand-official (`spec/dsh-client-ui-brand-official/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-brand-official/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-brand-official/frontend/`

### Package: @deepseek-ai/dsh-client-ui-chat (`spec/dsh-client-ui-chat/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-chat/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-chat/frontend/`

### Package: @deepseek-ai/dsh-client-ui-commands (`spec/dsh-client-ui-commands/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-commands/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-commands/frontend/`

### Package: @deepseek-ai/dsh-client-ui-context-menu (`spec/dsh-client-ui-context-menu/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-context-menu/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-context-menu/frontend/`

### Package: @deepseek-ai/dsh-client-ui-conversation (`spec/dsh-client-ui-conversation/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-conversation/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-conversation/frontend/`

### Package: @deepseek-ai/dsh-client-ui-deliverables (`spec/dsh-client-ui-deliverables/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-deliverables/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-deliverables/frontend/`

### Package: @deepseek-ai/dsh-client-ui-directory-picker-browse (`spec/dsh-client-ui-directory-picker-browse/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-directory-picker-browse/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-directory-picker-browse/frontend/`

### Package: @deepseek-ai/dsh-client-ui-directory-picker-native (`spec/dsh-client-ui-directory-picker-native/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-directory-picker-native/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-directory-picker-native/frontend/`

### Package: @deepseek-ai/dsh-client-ui-dockkit (`spec/dsh-client-ui-dockkit/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-dockkit/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-dockkit/frontend/`

### Package: @deepseek-ai/dsh-client-ui-entry-customization (`spec/dsh-client-ui-entry-customization/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-entry-customization/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-entry-customization/frontend/`

### Package: @deepseek-ai/dsh-client-ui-file-actions (`spec/dsh-client-ui-file-actions/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-file-actions/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-file-actions/frontend/`

### Package: @deepseek-ai/dsh-client-ui-file-drag (`spec/dsh-client-ui-file-drag/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-file-drag/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-file-drag/frontend/`

### Package: @deepseek-ai/dsh-client-ui-goal (`spec/dsh-client-ui-goal/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-goal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-goal/frontend/`

### Package: @deepseek-ai/dsh-client-ui-input-trigger (`spec/dsh-client-ui-input-trigger/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-input-trigger/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-input-trigger/frontend/`

### Package: @deepseek-ai/dsh-client-ui-jobs (`spec/dsh-client-ui-jobs/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-jobs/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-jobs/frontend/`

### Package: @deepseek-ai/dsh-client-ui-layout (`spec/dsh-client-ui-layout/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-layout/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-layout/frontend/`

### Package: @deepseek-ai/dsh-client-ui-message-feedback (`spec/dsh-client-ui-message-feedback/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-message-feedback/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-message-feedback/frontend/`

### Package: @deepseek-ai/dsh-client-ui-model-selection (`spec/dsh-client-ui-model-selection/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-model-selection/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-model-selection/frontend/`

### Package: @deepseek-ai/dsh-client-ui-open-in-app (`spec/dsh-client-ui-open-in-app/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-open-in-app/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-open-in-app/frontend/`

### Package: @deepseek-ai/dsh-client-ui-permission-presets (`spec/dsh-client-ui-permission-presets/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-permission-presets/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-permission-presets/frontend/`

### Package: @deepseek-ai/dsh-client-ui-plan (`spec/dsh-client-ui-plan/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-plan/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-plan/frontend/`

### Package: @deepseek-ai/dsh-client-ui-plugin-manager (`spec/dsh-client-ui-plugin-manager/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-plugin-manager/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-plugin-manager/frontend/`

### Package: @deepseek-ai/dsh-client-ui-plugin-market (`spec/dsh-client-ui-plugin-market/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-plugin-market/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-plugin-market/frontend/`

### Package: @deepseek-ai/dsh-client-ui-primitives (`spec/dsh-client-ui-primitives/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-primitives/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-primitives/frontend/`

### Package: @deepseek-ai/dsh-client-ui-reference (`spec/dsh-client-ui-reference/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-reference/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-reference/frontend/`

### Package: @deepseek-ai/dsh-client-ui-renderer (`spec/dsh-client-ui-renderer/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-renderer/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-renderer/frontend/`

### Package: @deepseek-ai/dsh-client-ui-schedule (`spec/dsh-client-ui-schedule/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-schedule/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-schedule/frontend/`

### Package: @deepseek-ai/dsh-client-ui-secret-mask (`spec/dsh-client-ui-secret-mask/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-secret-mask/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-secret-mask/frontend/`

### Package: @deepseek-ai/dsh-client-ui-session (`spec/dsh-client-ui-session/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-session/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-session/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings (`spec/dsh-client-ui-settings/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-account (`spec/dsh-client-ui-settings-account/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-account/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-account/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-agent-loop (`spec/dsh-client-ui-settings-agent-loop/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-agent-loop/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-agent-loop/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-general (`spec/dsh-client-ui-settings-general/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-general/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-general/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-models (`spec/dsh-client-ui-settings-models/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-models/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-models/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-plugin-inventory (`spec/dsh-client-ui-settings-plugin-inventory/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-plugin-inventory/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-plugin-inventory/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-plugins (`spec/dsh-client-ui-settings-plugins/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-plugins/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-plugins/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-session-log (`spec/dsh-client-ui-settings-session-log/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-session-log/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-session-log/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-shell (`spec/dsh-client-ui-settings-shell/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-shell/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-shell/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-subagent (`spec/dsh-client-ui-settings-subagent/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-subagent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-subagent/frontend/`

### Package: @deepseek-ai/dsh-client-ui-settings-web-search (`spec/dsh-client-ui-settings-web-search/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-settings-web-search/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-settings-web-search/frontend/`

### Package: @deepseek-ai/dsh-client-ui-shortcuts (`spec/dsh-client-ui-shortcuts/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-shortcuts/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-shortcuts/frontend/`

### Package: @deepseek-ai/dsh-client-ui-sidebar (`spec/dsh-client-ui-sidebar/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-sidebar/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-sidebar/frontend/`

### Package: @deepseek-ai/dsh-client-ui-sidebar-browser (`spec/dsh-client-ui-sidebar-browser/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-sidebar-browser/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-sidebar-browser/frontend/`

### Package: @deepseek-ai/dsh-client-ui-sidebar-documentpreview (`spec/dsh-client-ui-sidebar-documentpreview/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-sidebar-documentpreview/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-sidebar-documentpreview/frontend/`

### Package: @deepseek-ai/dsh-client-ui-sidebar-files (`spec/dsh-client-ui-sidebar-files/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-sidebar-files/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-sidebar-files/frontend/`

### Package: @deepseek-ai/dsh-client-ui-sidebar-right (`spec/dsh-client-ui-sidebar-right/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-sidebar-right/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-sidebar-right/frontend/`

### Package: @deepseek-ai/dsh-client-ui-sidebar-terminal (`spec/dsh-client-ui-sidebar-terminal/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-sidebar-terminal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-sidebar-terminal/frontend/`

### Package: @deepseek-ai/dsh-client-ui-skill (`spec/dsh-client-ui-skill/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-skill/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-skill/frontend/`

### Package: @deepseek-ai/dsh-client-ui-slots (`spec/dsh-client-ui-slots/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-slots/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-slots/frontend/`

### Package: @deepseek-ai/dsh-client-ui-subagent (`spec/dsh-client-ui-subagent/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-subagent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-subagent/frontend/`

### Package: @deepseek-ai/dsh-client-ui-theme (`spec/dsh-client-ui-theme/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-theme/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-theme/frontend/`

### Package: @deepseek-ai/dsh-client-ui-tool (`spec/dsh-client-ui-tool/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-tool/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-tool/frontend/`

### Package: @deepseek-ai/dsh-client-ui-trajectory (`spec/dsh-client-ui-trajectory/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-trajectory/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-trajectory/frontend/`

### Package: @deepseek-ai/dsh-client-ui-user-questions (`spec/dsh-client-ui-user-questions/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-user-questions/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-user-questions/frontend/`

### Package: @deepseek-ai/dsh-client-ui-workflow-run (`spec/dsh-client-ui-workflow-run/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-workflow-run/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-workflow-run/frontend/`

### Package: @deepseek-ai/dsh-client-ui-workspace (`spec/dsh-client-ui-workspace/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-workspace/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-workspace/frontend/`

### Package: @deepseek-ai/dsh-client-web (`spec/dsh-client-web/`)

- Backend guidelines: `.trellis/spec/dsh-client-web/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-web/frontend/`

### Package: @deepseek-ai/dsh-command-compact (`spec/dsh-command-compact/`)

- Backend guidelines: `.trellis/spec/dsh-command-compact/backend/`

- Frontend guidelines: `.trellis/spec/dsh-command-compact/frontend/`

### Package: @deepseek-ai/dsh-compaction (`spec/dsh-compaction/`)

- Backend guidelines: `.trellis/spec/dsh-compaction/backend/`

- Frontend guidelines: `.trellis/spec/dsh-compaction/frontend/`

### Package: @deepseek-ai/dsh-compaction-basic (`spec/dsh-compaction-basic/`)

- Backend guidelines: `.trellis/spec/dsh-compaction-basic/backend/`

- Frontend guidelines: `.trellis/spec/dsh-compaction-basic/frontend/`

### Package: @deepseek-ai/dsh-compaction-image-offload (`spec/dsh-compaction-image-offload/`)

- Backend guidelines: `.trellis/spec/dsh-compaction-image-offload/backend/`

- Frontend guidelines: `.trellis/spec/dsh-compaction-image-offload/frontend/`

### Package: @deepseek-ai/dsh-compaction-tool-result-pruner (`spec/dsh-compaction-tool-result-pruner/`)

- Backend guidelines: `.trellis/spec/dsh-compaction-tool-result-pruner/backend/`

- Frontend guidelines: `.trellis/spec/dsh-compaction-tool-result-pruner/frontend/`

### Package: @deepseek-ai/dsh-computer-use (`spec/dsh-computer-use/`)

- Backend guidelines: `.trellis/spec/dsh-computer-use/backend/`

- Frontend guidelines: `.trellis/spec/dsh-computer-use/frontend/`

### Package: @deepseek-ai/dsh-agent-instructions (`spec/dsh-agent-instructions/`)

- Backend guidelines: `.trellis/spec/dsh-agent-instructions/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-instructions/frontend/`

### Package: @deepseek-ai/dsh-file-reference (`spec/dsh-file-reference/`)

- Backend guidelines: `.trellis/spec/dsh-file-reference/backend/`

- Frontend guidelines: `.trellis/spec/dsh-file-reference/frontend/`

### Package: @deepseek-ai/dsh-file-reference-local (`spec/dsh-file-reference-local/`)

- Backend guidelines: `.trellis/spec/dsh-file-reference-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-file-reference-local/frontend/`

### Package: @deepseek-ai/dsh-harness-dev-context (`spec/dsh-harness-dev-context/`)

- Backend guidelines: `.trellis/spec/dsh-harness-dev-context/backend/`

- Frontend guidelines: `.trellis/spec/dsh-harness-dev-context/frontend/`

### Package: @deepseek-ai/dsh-session-reference (`spec/dsh-session-reference/`)

- Backend guidelines: `.trellis/spec/dsh-session-reference/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-reference/frontend/`

### Package: @deepseek-ai/dsh-time-context (`spec/dsh-time-context/`)

- Backend guidelines: `.trellis/spec/dsh-time-context/backend/`

- Frontend guidelines: `.trellis/spec/dsh-time-context/frontend/`

### Package: @deepseek-ai/dsh-tmux-context (`spec/dsh-tmux-context/`)

- Backend guidelines: `.trellis/spec/dsh-tmux-context/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tmux-context/frontend/`

### Package: @deepseek-ai/dsh-agent (`spec/dsh-agent/`)

- Backend guidelines: `.trellis/spec/dsh-agent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent/frontend/`

### Package: @deepseek-ai/dsh-agent-default-model (`spec/dsh-agent-default-model/`)

- Backend guidelines: `.trellis/spec/dsh-agent-default-model/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-default-model/frontend/`

### Package: @deepseek-ai/dsh-agent-loop (`spec/dsh-agent-loop/`)

- Backend guidelines: `.trellis/spec/dsh-agent-loop/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-loop/frontend/`

### Package: @deepseek-ai/dsh-agent-tool-presentation (`spec/dsh-agent-tool-presentation/`)

- Backend guidelines: `.trellis/spec/dsh-agent-tool-presentation/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-tool-presentation/frontend/`

### Package: @deepseek-ai/dsh-scope (`spec/dsh-scope/`)

- Backend guidelines: `.trellis/spec/dsh-scope/backend/`

- Frontend guidelines: `.trellis/spec/dsh-scope/frontend/`

### Package: @deepseek-ai/dsh-session (`spec/dsh-session/`)

- Backend guidelines: `.trellis/spec/dsh-session/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session/frontend/`

### Package: @deepseek-ai/dsh-system-prompt (`spec/dsh-system-prompt/`)

- Backend guidelines: `.trellis/spec/dsh-system-prompt/backend/`

- Frontend guidelines: `.trellis/spec/dsh-system-prompt/frontend/`

### Package: @deepseek-ai/dsh-tool-executor-native (`spec/dsh-tool-executor-native/`)

- Backend guidelines: `.trellis/spec/dsh-tool-executor-native/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-executor-native/frontend/`

### Package: @deepseek-ai/dsh-tool-executor-ptc (`spec/dsh-tool-executor-ptc/`)

- Backend guidelines: `.trellis/spec/dsh-tool-executor-ptc/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-executor-ptc/frontend/`

### Package: @deepseek-ai/dsh-tools (`spec/dsh-tools/`)

- Backend guidelines: `.trellis/spec/dsh-tools/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tools/frontend/`

### Package: @deepseek-ai/dsh-authorization (`spec/dsh-authorization/`)

- Backend guidelines: `.trellis/spec/dsh-authorization/backend/`

- Frontend guidelines: `.trellis/spec/dsh-authorization/frontend/`

### Package: @deepseek-ai/dsh-credentials (`spec/dsh-credentials/`)

- Backend guidelines: `.trellis/spec/dsh-credentials/backend/`

- Frontend guidelines: `.trellis/spec/dsh-credentials/frontend/`

### Package: @deepseek-ai/dsh-credentials-local (`spec/dsh-credentials-local/`)

- Backend guidelines: `.trellis/spec/dsh-credentials-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-credentials-local/frontend/`

### Package: @deepseek-ai/dsh-deepseek-account (`spec/dsh-deepseek-account/`)

- Backend guidelines: `.trellis/spec/dsh-deepseek-account/backend/`

- Frontend guidelines: `.trellis/spec/dsh-deepseek-account/frontend/`

### Package: @deepseek-ai/dsh-deepseek-account-platform (`spec/dsh-deepseek-account-platform/`)

- Backend guidelines: `.trellis/spec/dsh-deepseek-account-platform/backend/`

- Frontend guidelines: `.trellis/spec/dsh-deepseek-account-platform/frontend/`

### Package: @deepseek-ai/dsh-deliverable-file-references (`spec/dsh-deliverable-file-references/`)

- Backend guidelines: `.trellis/spec/dsh-deliverable-file-references/backend/`

- Frontend guidelines: `.trellis/spec/dsh-deliverable-file-references/frontend/`

### Package: @deepseek-ai/dsh-tool-present (`spec/dsh-tool-present/`)

- Backend guidelines: `.trellis/spec/dsh-tool-present/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-present/frontend/`

### Package: @deepseek-ai/dsh-workspace-changes (`spec/dsh-workspace-changes/`)

- Backend guidelines: `.trellis/spec/dsh-workspace-changes/backend/`

- Frontend guidelines: `.trellis/spec/dsh-workspace-changes/frontend/`

### Package: @deepseek-ai/dsh-office-to-pdf (`spec/dsh-office-to-pdf/`)

- Backend guidelines: `.trellis/spec/dsh-office-to-pdf/backend/`

- Frontend guidelines: `.trellis/spec/dsh-office-to-pdf/frontend/`

### Package: @deepseek-ai/dsh-action-cards (`spec/dsh-action-cards/`)

- Backend guidelines: `.trellis/spec/dsh-action-cards/backend/`

- Frontend guidelines: `.trellis/spec/dsh-action-cards/frontend/`

### Package: @deepseek-ai/dsh-experimental-api-speech-to-text (`spec/dsh-experimental-api-speech-to-text/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-api-speech-to-text/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-api-speech-to-text/frontend/`

### Package: @deepseek-ai/dsh-experimental-auto-review (`spec/dsh-experimental-auto-review/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-auto-review/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-auto-review/frontend/`

### Package: @deepseek-ai/dsh-experimental-badge-skill-bundle (`spec/dsh-experimental-badge-skill-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-badge-skill-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-badge-skill-bundle/frontend/`

### Package: @deepseek-ai/dsh-experimental-browser-use-chrome-devtools-mcp (`spec/dsh-experimental-browser-use-chrome-devtools-mcp/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-browser-use-chrome-devtools-mcp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-browser-use-chrome-devtools-mcp/frontend/`

### Package: @deepseek-ai/dsh-experimental-browser-use-playwright-mcp (`spec/dsh-experimental-browser-use-playwright-mcp/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-browser-use-playwright-mcp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-browser-use-playwright-mcp/frontend/`

### Package: @deepseek-ai/dsh-experimental-browser-use-runtime (`spec/dsh-experimental-browser-use-runtime/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-browser-use-runtime/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-browser-use-runtime/frontend/`

### Package: @deepseek-ai/dsh-experimental-browser-use-stagehand-native (`spec/dsh-experimental-browser-use-stagehand-native/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-browser-use-stagehand-native/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-browser-use-stagehand-native/frontend/`

### Package: @deepseek-ai/dsh-experimental-claude-code-mods (`spec/dsh-experimental-claude-code-mods/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-claude-code-mods/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-claude-code-mods/frontend/`

### Package: @deepseek-ai/dsh-client-ui-action-cards (`spec/dsh-client-ui-action-cards/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-action-cards/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-action-cards/frontend/`

### Package: @deepseek-ai/dsh-experimental-client-ui-claude-code-mods (`spec/dsh-experimental-client-ui-claude-code-mods/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-client-ui-claude-code-mods/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-client-ui-claude-code-mods/frontend/`

### Package: @deepseek-ai/dsh-experimental-client-ui-cot-translation (`spec/dsh-experimental-client-ui-cot-translation/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-client-ui-cot-translation/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-client-ui-cot-translation/frontend/`

### Package: @deepseek-ai/dsh-client-ui-creation-recommendations (`spec/dsh-client-ui-creation-recommendations/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-creation-recommendations/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-creation-recommendations/frontend/`

### Package: @deepseek-ai/dsh-experimental-client-ui-forge (`spec/dsh-experimental-client-ui-forge/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-client-ui-forge/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-client-ui-forge/frontend/`

### Package: @deepseek-ai/dsh-client-ui-plugin-recommendations (`spec/dsh-client-ui-plugin-recommendations/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-plugin-recommendations/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-plugin-recommendations/frontend/`

### Package: @deepseek-ai/dsh-experimental-client-ui-stats (`spec/dsh-experimental-client-ui-stats/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-client-ui-stats/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-client-ui-stats/frontend/`

### Package: @deepseek-ai/dsh-experimental-client-ui-voice-input (`spec/dsh-experimental-client-ui-voice-input/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-client-ui-voice-input/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-client-ui-voice-input/frontend/`

### Package: @deepseek-ai/dsh-experimental-computer-use-cua-driver-mcp (`spec/dsh-experimental-computer-use-cua-driver-mcp/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-computer-use-cua-driver-mcp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-computer-use-cua-driver-mcp/frontend/`

### Package: @deepseek-ai/dsh-experimental-computer-use-cua-driver-native (`spec/dsh-experimental-computer-use-cua-driver-native/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-computer-use-cua-driver-native/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-computer-use-cua-driver-native/frontend/`

### Package: @deepseek-ai/dsh-experimental-cot-translation-bundle (`spec/dsh-experimental-cot-translation-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-cot-translation-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-cot-translation-bundle/frontend/`

### Package: @deepseek-ai/dsh-creation-recommendations (`spec/dsh-creation-recommendations/`)

- Backend guidelines: `.trellis/spec/dsh-creation-recommendations/backend/`

- Frontend guidelines: `.trellis/spec/dsh-creation-recommendations/frontend/`

### Package: @deepseek-ai/dsh-cua (`spec/dsh-cua/`)

- Backend guidelines: `.trellis/spec/dsh-cua/backend/`

- Frontend guidelines: `.trellis/spec/dsh-cua/frontend/`

### Package: @deepseek-ai/dsh-cua-bundle (`spec/dsh-cua-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-cua-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-cua-bundle/frontend/`

### Package: @deepseek-ai/dsh-experimental-cua-macos (`spec/dsh-experimental-cua-macos/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-cua-macos/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-cua-macos/frontend/`

### Package: @deepseek-ai/dsh-experimental-forge (`spec/dsh-experimental-forge/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-forge/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-forge/frontend/`

### Package: @deepseek-ai/dsh-experimental-forge-bundle (`spec/dsh-experimental-forge-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-forge-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-forge-bundle/frontend/`

### Package: @deepseek-ai/dsh-experimental-forge-github (`spec/dsh-experimental-forge-github/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-forge-github/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-forge-github/frontend/`

### Package: @deepseek-ai/dsh-experimental-forge-session (`spec/dsh-experimental-forge-session/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-forge-session/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-forge-session/frontend/`

### Package: @deepseek-ai/dsh-hook-protocol (`spec/dsh-hook-protocol/`)

- Backend guidelines: `.trellis/spec/dsh-hook-protocol/backend/`

- Frontend guidelines: `.trellis/spec/dsh-hook-protocol/frontend/`

### Package: @deepseek-ai/dsh-hooks-claude-code (`spec/dsh-hooks-claude-code/`)

- Backend guidelines: `.trellis/spec/dsh-hooks-claude-code/backend/`

- Frontend guidelines: `.trellis/spec/dsh-hooks-claude-code/frontend/`

### Package: @deepseek-ai/dsh-hooks-codex (`spec/dsh-hooks-codex/`)

- Backend guidelines: `.trellis/spec/dsh-hooks-codex/backend/`

- Frontend guidelines: `.trellis/spec/dsh-hooks-codex/frontend/`

### Package: @deepseek-ai/dsh-experimental-inspector (`spec/dsh-experimental-inspector/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-inspector/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-inspector/frontend/`

### Package: @deepseek-ai/dsh-experimental-inspector-profile (`spec/dsh-experimental-inspector-profile/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-inspector-profile/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-inspector-profile/frontend/`

### Package: @deepseek-ai/dsh-experimental-liveshare (`spec/dsh-experimental-liveshare/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-liveshare/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-liveshare/frontend/`

### Package: @deepseek-ai/dsh-experimental-liveshare-protocol (`spec/dsh-experimental-liveshare-protocol/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-liveshare-protocol/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-liveshare-protocol/frontend/`

### Package: @deepseek-ai/dsh-personalized-recommendations (`spec/dsh-personalized-recommendations/`)

- Backend guidelines: `.trellis/spec/dsh-personalized-recommendations/backend/`

- Frontend guidelines: `.trellis/spec/dsh-personalized-recommendations/frontend/`

### Package: @deepseek-ai/dsh-experimental-plugin-market-bundle (`spec/dsh-experimental-plugin-market-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-plugin-market-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-plugin-market-bundle/frontend/`

### Package: @deepseek-ai/dsh-plugin-recommendations (`spec/dsh-plugin-recommendations/`)

- Backend guidelines: `.trellis/spec/dsh-plugin-recommendations/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plugin-recommendations/frontend/`

### Package: @deepseek-ai/dsh-experimental-ptc-runtime-python (`spec/dsh-experimental-ptc-runtime-python/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-ptc-runtime-python/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-ptc-runtime-python/frontend/`

### Package: @deepseek-ai/dsh-experimental-ralph-bundle (`spec/dsh-experimental-ralph-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-ralph-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-ralph-bundle/frontend/`

### Package: @deepseek-ai/dsh-experimental-session-inspector (`spec/dsh-experimental-session-inspector/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-session-inspector/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-session-inspector/frontend/`

### Package: @deepseek-ai/dsh-experimental-session-search (`spec/dsh-experimental-session-search/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-session-search/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-session-search/frontend/`

### Package: @deepseek-ai/dsh-session-title-all-prompts-llm (`spec/dsh-session-title-all-prompts-llm/`)

- Backend guidelines: `.trellis/spec/dsh-session-title-all-prompts-llm/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-title-all-prompts-llm/frontend/`

### Package: @deepseek-ai/dsh-experimental-session-titles-bundle (`spec/dsh-experimental-session-titles-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-session-titles-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-session-titles-bundle/frontend/`

### Package: @deepseek-ai/dsh-skill-badge (`spec/dsh-skill-badge/`)

- Backend guidelines: `.trellis/spec/dsh-skill-badge/backend/`

- Frontend guidelines: `.trellis/spec/dsh-skill-badge/frontend/`

### Package: @deepseek-ai/dsh-experimental-speech-to-text (`spec/dsh-experimental-speech-to-text/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-speech-to-text/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-speech-to-text/frontend/`

### Package: @deepseek-ai/dsh-experimental-speech-to-text-sensevoice (`spec/dsh-experimental-speech-to-text-sensevoice/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-speech-to-text-sensevoice/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-speech-to-text-sensevoice/frontend/`

### Package: @deepseek-ai/dsh-experimental-subagent-oar (`spec/dsh-experimental-subagent-oar/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-subagent-oar/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-subagent-oar/frontend/`

### Package: @deepseek-ai/dsh-experimental-terminal-bundle (`spec/dsh-experimental-terminal-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-terminal-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-terminal-bundle/frontend/`

### Package: @deepseek-ai/dsh-tool-ralph (`spec/dsh-tool-ralph/`)

- Backend guidelines: `.trellis/spec/dsh-tool-ralph/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-ralph/frontend/`

### Package: @deepseek-ai/dsh-tool-session-query (`spec/dsh-tool-session-query/`)

- Backend guidelines: `.trellis/spec/dsh-tool-session-query/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-session-query/frontend/`

### Package: @deepseek-ai/dsh-experimental-tool-subagent-oar (`spec/dsh-experimental-tool-subagent-oar/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-tool-subagent-oar/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-tool-subagent-oar/frontend/`

### Package: @deepseek-ai/dsh-tool-terminal (`spec/dsh-tool-terminal/`)

- Backend guidelines: `.trellis/spec/dsh-tool-terminal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-terminal/frontend/`

### Package: @deepseek-ai/dsh-experimental-tool-worktree (`spec/dsh-experimental-tool-worktree/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-tool-worktree/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-tool-worktree/frontend/`

### Package: @deepseek-ai/dsh-experimental-translator (`spec/dsh-experimental-translator/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-translator/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-translator/frontend/`

### Package: @deepseek-ai/dsh-experimental-voice-input-bundle (`spec/dsh-experimental-voice-input-bundle/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-voice-input-bundle/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-voice-input-bundle/frontend/`

### Package: @deepseek-ai/dsh-webhook (`spec/dsh-webhook/`)

- Backend guidelines: `.trellis/spec/dsh-webhook/backend/`

- Frontend guidelines: `.trellis/spec/dsh-webhook/frontend/`

### Package: @deepseek-ai/dsh-webhook-github (`spec/dsh-webhook-github/`)

- Backend guidelines: `.trellis/spec/dsh-webhook-github/backend/`

- Frontend guidelines: `.trellis/spec/dsh-webhook-github/frontend/`

### Package: @deepseek-ai/dsh-experimental-webworker-packer (`spec/dsh-experimental-webworker-packer/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-webworker-packer/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-webworker-packer/frontend/`

### Package: @deepseek-ai/dsh-experimental-webworker-runtime (`spec/dsh-experimental-webworker-runtime/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-webworker-runtime/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-webworker-runtime/frontend/`

### Package: @deepseek-ai/dsh-experimental-worktree (`spec/dsh-experimental-worktree/`)

- Backend guidelines: `.trellis/spec/dsh-experimental-worktree/backend/`

- Frontend guidelines: `.trellis/spec/dsh-experimental-worktree/frontend/`

### Package: @deepseek-ai/dsh-cordis-client-runner (`spec/dsh-cordis-client-runner/`)

- Backend guidelines: `.trellis/spec/dsh-cordis-client-runner/backend/`

- Frontend guidelines: `.trellis/spec/dsh-cordis-client-runner/frontend/`

### Package: @deepseek-ai/dsh-cordis-host-runner (`spec/dsh-cordis-host-runner/`)

- Backend guidelines: `.trellis/spec/dsh-cordis-host-runner/backend/`

- Frontend guidelines: `.trellis/spec/dsh-cordis-host-runner/frontend/`

### Package: @deepseek-ai/dsh-tool-cordis (`spec/dsh-tool-cordis/`)

- Backend guidelines: `.trellis/spec/dsh-tool-cordis/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-cordis/frontend/`

### Package: @deepseek-ai/dsh-client-ui-cordis (`spec/dsh-client-ui-cordis/`)

- Backend guidelines: `.trellis/spec/dsh-client-ui-cordis/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-ui-cordis/frontend/`

### Package: @deepseek-ai/dsh-command-feedback (`spec/dsh-command-feedback/`)

- Backend guidelines: `.trellis/spec/dsh-command-feedback/backend/`

- Frontend guidelines: `.trellis/spec/dsh-command-feedback/frontend/`

### Package: @deepseek-ai/dsh-message-feedback (`spec/dsh-message-feedback/`)

- Backend guidelines: `.trellis/spec/dsh-message-feedback/backend/`

- Frontend guidelines: `.trellis/spec/dsh-message-feedback/frontend/`

### Package: @deepseek-ai/dsh-fs (`spec/dsh-fs/`)

- Backend guidelines: `.trellis/spec/dsh-fs/backend/`

- Frontend guidelines: `.trellis/spec/dsh-fs/frontend/`

### Package: @deepseek-ai/dsh-fs-local (`spec/dsh-fs-local/`)

- Backend guidelines: `.trellis/spec/dsh-fs-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-fs-local/frontend/`

### Package: @deepseek-ai/dsh-fs-observation-policy (`spec/dsh-fs-observation-policy/`)

- Backend guidelines: `.trellis/spec/dsh-fs-observation-policy/backend/`

- Frontend guidelines: `.trellis/spec/dsh-fs-observation-policy/frontend/`

### Package: @deepseek-ai/dsh-fs-patch (`spec/dsh-fs-patch/`)

- Backend guidelines: `.trellis/spec/dsh-fs-patch/backend/`

- Frontend guidelines: `.trellis/spec/dsh-fs-patch/frontend/`

### Package: @deepseek-ai/dsh-fs-sandbox (`spec/dsh-fs-sandbox/`)

- Backend guidelines: `.trellis/spec/dsh-fs-sandbox/backend/`

- Frontend guidelines: `.trellis/spec/dsh-fs-sandbox/frontend/`

### Package: @deepseek-ai/dsh-tool-fs (`spec/dsh-tool-fs/`)

- Backend guidelines: `.trellis/spec/dsh-tool-fs/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-fs/frontend/`

### Package: @deepseek-ai/dsh-tool-fs-search (`spec/dsh-tool-fs-search/`)

- Backend guidelines: `.trellis/spec/dsh-tool-fs-search/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-fs-search/frontend/`

### Package: @deepseek-ai/dsh-tool-str-replace-editor (`spec/dsh-tool-str-replace-editor/`)

- Backend guidelines: `.trellis/spec/dsh-tool-str-replace-editor/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-str-replace-editor/frontend/`

### Package: @deepseek-ai/dsh-command-goal (`spec/dsh-command-goal/`)

- Backend guidelines: `.trellis/spec/dsh-command-goal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-command-goal/frontend/`

### Package: @deepseek-ai/dsh-goal (`spec/dsh-goal/`)

- Backend guidelines: `.trellis/spec/dsh-goal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-goal/frontend/`

### Package: @deepseek-ai/dsh-goal-round-driver (`spec/dsh-goal-round-driver/`)

- Backend guidelines: `.trellis/spec/dsh-goal-round-driver/backend/`

- Frontend guidelines: `.trellis/spec/dsh-goal-round-driver/frontend/`

### Package: @deepseek-ai/dsh-tool-goal (`spec/dsh-tool-goal/`)

- Backend guidelines: `.trellis/spec/dsh-tool-goal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-goal/frontend/`

### Package: @deepseek-ai/dsh-repeat-tool-reminder (`spec/dsh-repeat-tool-reminder/`)

- Backend guidelines: `.trellis/spec/dsh-repeat-tool-reminder/backend/`

- Frontend guidelines: `.trellis/spec/dsh-repeat-tool-reminder/frontend/`

### Package: @deepseek-ai/dsh-tool-call-timeout-policy (`spec/dsh-tool-call-timeout-policy/`)

- Backend guidelines: `.trellis/spec/dsh-tool-call-timeout-policy/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-call-timeout-policy/frontend/`

### Package: @deepseek-ai/dsh-host-directory-picker (`spec/dsh-host-directory-picker/`)

- Backend guidelines: `.trellis/spec/dsh-host-directory-picker/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-directory-picker/frontend/`

### Package: @deepseek-ai/dsh-host-directory-picker-auto (`spec/dsh-host-directory-picker-auto/`)

- Backend guidelines: `.trellis/spec/dsh-host-directory-picker-auto/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-directory-picker-auto/frontend/`

### Package: @deepseek-ai/dsh-host-directory-picker-browse (`spec/dsh-host-directory-picker-browse/`)

- Backend guidelines: `.trellis/spec/dsh-host-directory-picker-browse/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-directory-picker-browse/frontend/`

### Package: @deepseek-ai/dsh-host-directory-picker-native (`spec/dsh-host-directory-picker-native/`)

- Backend guidelines: `.trellis/spec/dsh-host-directory-picker-native/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-directory-picker-native/frontend/`

### Package: @deepseek-ai/dsh-host-frontend-static (`spec/dsh-host-frontend-static/`)

- Backend guidelines: `.trellis/spec/dsh-host-frontend-static/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-frontend-static/frontend/`

### Package: @deepseek-ai/dsh-host-open-in-app (`spec/dsh-host-open-in-app/`)

- Backend guidelines: `.trellis/spec/dsh-host-open-in-app/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-open-in-app/frontend/`

### Package: @deepseek-ai/dsh-host-plugin-inventory (`spec/dsh-host-plugin-inventory/`)

- Backend guidelines: `.trellis/spec/dsh-host-plugin-inventory/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-plugin-inventory/frontend/`

### Package: @deepseek-ai/dsh-host-product-telemetry-otel (`spec/dsh-host-product-telemetry-otel/`)

- Backend guidelines: `.trellis/spec/dsh-host-product-telemetry-otel/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-product-telemetry-otel/frontend/`

### Package: @deepseek-ai/dsh-host-webserver (`spec/dsh-host-webserver/`)

- Backend guidelines: `.trellis/spec/dsh-host-webserver/backend/`

- Frontend guidelines: `.trellis/spec/dsh-host-webserver/frontend/`

### Package: @deepseek-ai/dsh-anonymous-user-id (`spec/dsh-anonymous-user-id/`)

- Backend guidelines: `.trellis/spec/dsh-anonymous-user-id/backend/`

- Frontend guidelines: `.trellis/spec/dsh-anonymous-user-id/frontend/`

### Package: @deepseek-ai/dsh-commands (`spec/dsh-commands/`)

- Backend guidelines: `.trellis/spec/dsh-commands/backend/`

- Frontend guidelines: `.trellis/spec/dsh-commands/frontend/`

### Package: @deepseek-ai/dsh-permission-presets (`spec/dsh-permission-presets/`)

- Backend guidelines: `.trellis/spec/dsh-permission-presets/backend/`

- Frontend guidelines: `.trellis/spec/dsh-permission-presets/frontend/`

### Package: @deepseek-ai/dsh-tool-ask-user (`spec/dsh-tool-ask-user/`)

- Backend guidelines: `.trellis/spec/dsh-tool-ask-user/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-ask-user/frontend/`

### Package: @deepseek-ai/dsh-user-approval (`spec/dsh-user-approval/`)

- Backend guidelines: `.trellis/spec/dsh-user-approval/backend/`

- Frontend guidelines: `.trellis/spec/dsh-user-approval/frontend/`

### Package: @deepseek-ai/dsh-user-questions (`spec/dsh-user-questions/`)

- Backend guidelines: `.trellis/spec/dsh-user-questions/backend/`

- Frontend guidelines: `.trellis/spec/dsh-user-questions/frontend/`

### Package: @deepseek-ai/dsh-jobs (`spec/dsh-jobs/`)

- Backend guidelines: `.trellis/spec/dsh-jobs/backend/`

- Frontend guidelines: `.trellis/spec/dsh-jobs/frontend/`

### Package: @deepseek-ai/dsh-jobs-local (`spec/dsh-jobs-local/`)

- Backend guidelines: `.trellis/spec/dsh-jobs-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-jobs-local/frontend/`

### Package: @deepseek-ai/dsh-tool-jobs (`spec/dsh-tool-jobs/`)

- Backend guidelines: `.trellis/spec/dsh-tool-jobs/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-jobs/frontend/`

### Package: @deepseek-ai/dsh-deepseek-llm-api-extensions (`spec/dsh-deepseek-llm-api-extensions/`)

- Backend guidelines: `.trellis/spec/dsh-deepseek-llm-api-extensions/backend/`

- Frontend guidelines: `.trellis/spec/dsh-deepseek-llm-api-extensions/frontend/`

### Package: @deepseek-ai/dsh-llm (`spec/dsh-llm/`)

- Backend guidelines: `.trellis/spec/dsh-llm/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm/frontend/`

### Package: @deepseek-ai/dsh-llm-deepseek (`spec/dsh-llm-deepseek/`)

- Backend guidelines: `.trellis/spec/dsh-llm-deepseek/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-deepseek/frontend/`

### Package: @deepseek-ai/dsh-llm-deepseek-account (`spec/dsh-llm-deepseek-account/`)

- Backend guidelines: `.trellis/spec/dsh-llm-deepseek-account/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-deepseek-account/frontend/`

### Package: @deepseek-ai/dsh-llm-deepseek-api-key (`spec/dsh-llm-deepseek-api-key/`)

- Backend guidelines: `.trellis/spec/dsh-llm-deepseek-api-key/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-deepseek-api-key/frontend/`

### Package: @deepseek-ai/dsh-llm-pi-ai (`spec/dsh-llm-pi-ai/`)

- Backend guidelines: `.trellis/spec/dsh-llm-pi-ai/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-pi-ai/frontend/`

### Package: @deepseek-ai/dsh-llm-retry (`spec/dsh-llm-retry/`)

- Backend guidelines: `.trellis/spec/dsh-llm-retry/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-retry/frontend/`

### Package: @deepseek-ai/dsh-plugin-package-inventory-deepseek (`spec/dsh-plugin-package-inventory-deepseek/`)

- Backend guidelines: `.trellis/spec/dsh-plugin-package-inventory-deepseek/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plugin-package-inventory-deepseek/frontend/`

### Package: @deepseek-ai/dsh-token-meter (`spec/dsh-token-meter/`)

- Backend guidelines: `.trellis/spec/dsh-token-meter/backend/`

- Frontend guidelines: `.trellis/spec/dsh-token-meter/frontend/`

### Package: @deepseek-ai/dsh-lsp (`spec/dsh-lsp/`)

- Backend guidelines: `.trellis/spec/dsh-lsp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-lsp/frontend/`

### Package: @deepseek-ai/dsh-lsp-stdio (`spec/dsh-lsp-stdio/`)

- Backend guidelines: `.trellis/spec/dsh-lsp-stdio/backend/`

- Frontend guidelines: `.trellis/spec/dsh-lsp-stdio/frontend/`

### Package: @deepseek-ai/dsh-tool-lsp (`spec/dsh-tool-lsp/`)

- Backend guidelines: `.trellis/spec/dsh-tool-lsp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-lsp/frontend/`

### Package: @deepseek-ai/dsh-mcp-client (`spec/dsh-mcp-client/`)

- Backend guidelines: `.trellis/spec/dsh-mcp-client/backend/`

- Frontend guidelines: `.trellis/spec/dsh-mcp-client/frontend/`

### Package: @deepseek-ai/dsh-mcp-manager (`spec/dsh-mcp-manager/`)

- Backend guidelines: `.trellis/spec/dsh-mcp-manager/backend/`

- Frontend guidelines: `.trellis/spec/dsh-mcp-manager/frontend/`

### Package: @deepseek-ai/dsh-mcp-resources (`spec/dsh-mcp-resources/`)

- Backend guidelines: `.trellis/spec/dsh-mcp-resources/backend/`

- Frontend guidelines: `.trellis/spec/dsh-mcp-resources/frontend/`

### Package: @deepseek-ai/dsh-plan-mode (`spec/dsh-plan-mode/`)

- Backend guidelines: `.trellis/spec/dsh-plan-mode/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plan-mode/frontend/`

### Package: @deepseek-ai/dsh-agent-preset (`spec/dsh-agent-preset/`)

- Backend guidelines: `.trellis/spec/dsh-agent-preset/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-preset/frontend/`

### Package: @deepseek-ai/dsh-agent-preset-registry (`spec/dsh-agent-preset-registry/`)

- Backend guidelines: `.trellis/spec/dsh-agent-preset-registry/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-preset-registry/frontend/`

### Package: @deepseek-ai/dsh-persona (`spec/dsh-persona/`)

- Backend guidelines: `.trellis/spec/dsh-persona/backend/`

- Frontend guidelines: `.trellis/spec/dsh-persona/frontend/`

### Package: @deepseek-ai/dsh-ptc-runtime (`spec/dsh-ptc-runtime/`)

- Backend guidelines: `.trellis/spec/dsh-ptc-runtime/backend/`

- Frontend guidelines: `.trellis/spec/dsh-ptc-runtime/frontend/`

### Package: @deepseek-ai/dsh-ptc-runtime-node (`spec/dsh-ptc-runtime-node/`)

- Backend guidelines: `.trellis/spec/dsh-ptc-runtime-node/backend/`

- Frontend guidelines: `.trellis/spec/dsh-ptc-runtime-node/frontend/`

### Package: @deepseek-ai/dsh-sandbox (`spec/dsh-sandbox/`)

- Backend guidelines: `.trellis/spec/dsh-sandbox/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sandbox/frontend/`

### Package: @deepseek-ai/dsh-sandbox-local (`spec/dsh-sandbox-local/`)

- Backend guidelines: `.trellis/spec/dsh-sandbox-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sandbox-local/frontend/`

### Package: @deepseek-ai/dsh-sandbox-policy (`spec/dsh-sandbox-policy/`)

- Backend guidelines: `.trellis/spec/dsh-sandbox-policy/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sandbox-policy/frontend/`

### Package: @deepseek-ai/dsh-sandbox-windows-acl (`spec/dsh-sandbox-windows-acl/`)

- Backend guidelines: `.trellis/spec/dsh-sandbox-windows-acl/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sandbox-windows-acl/frontend/`

### Package: @deepseek-ai/dsh-schedule (`spec/dsh-schedule/`)

- Backend guidelines: `.trellis/spec/dsh-schedule/backend/`

- Frontend guidelines: `.trellis/spec/dsh-schedule/frontend/`

### Package: @deepseek-ai/dsh-tool-schedule (`spec/dsh-tool-schedule/`)

- Backend guidelines: `.trellis/spec/dsh-tool-schedule/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-schedule/frontend/`

### Package: @deepseek-ai/dsh-sdk-client (`spec/dsh-sdk-client/`)

- Backend guidelines: `.trellis/spec/dsh-sdk-client/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sdk-client/frontend/`

### Package: @deepseek-ai/dsh-sdk-protocol (`spec/dsh-sdk-protocol/`)

- Backend guidelines: `.trellis/spec/dsh-sdk-protocol/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sdk-protocol/frontend/`

### Package: @deepseek-ai/dsh-sdk-jsonrpc-server (`spec/dsh-sdk-jsonrpc-server/`)

- Backend guidelines: `.trellis/spec/dsh-sdk-jsonrpc-server/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sdk-jsonrpc-server/frontend/`

### Package: @deepseek-ai/dsh-message-quotes (`spec/dsh-message-quotes/`)

- Backend guidelines: `.trellis/spec/dsh-message-quotes/backend/`

- Frontend guidelines: `.trellis/spec/dsh-message-quotes/frontend/`

### Package: @deepseek-ai/dsh-session-checkpoint-policy (`spec/dsh-session-checkpoint-policy/`)

- Backend guidelines: `.trellis/spec/dsh-session-checkpoint-policy/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-checkpoint-policy/frontend/`

### Package: @deepseek-ai/dsh-session-format (`spec/dsh-session-format/`)

- Backend guidelines: `.trellis/spec/dsh-session-format/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-format/frontend/`

### Package: @deepseek-ai/dsh-session-format-catalog (`spec/dsh-session-format-catalog/`)

- Backend guidelines: `.trellis/spec/dsh-session-format-catalog/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-format-catalog/frontend/`

### Package: @deepseek-ai/dsh-session-format-v0-to-v1 (`spec/dsh-session-format-v0-to-v1/`)

- Backend guidelines: `.trellis/spec/dsh-session-format-v0-to-v1/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-format-v0-to-v1/frontend/`

### Package: @deepseek-ai/dsh-session-format-v1-to-v2 (`spec/dsh-session-format-v1-to-v2/`)

- Backend guidelines: `.trellis/spec/dsh-session-format-v1-to-v2/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-format-v1-to-v2/frontend/`

### Package: @deepseek-ai/dsh-session-format-v2-to-v3 (`spec/dsh-session-format-v2-to-v3/`)

- Backend guidelines: `.trellis/spec/dsh-session-format-v2-to-v3/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-format-v2-to-v3/frontend/`

### Package: @deepseek-ai/dsh-session-format-v3-to-v4 (`spec/dsh-session-format-v3-to-v4/`)

- Backend guidelines: `.trellis/spec/dsh-session-format-v3-to-v4/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-format-v3-to-v4/frontend/`

### Package: @deepseek-ai/dsh-session-log-deepseek (`spec/dsh-session-log-deepseek/`)

- Backend guidelines: `.trellis/spec/dsh-session-log-deepseek/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-log-deepseek/frontend/`

### Package: @deepseek-ai/dsh-session-persistence (`spec/dsh-session-persistence/`)

- Backend guidelines: `.trellis/spec/dsh-session-persistence/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-persistence/frontend/`

### Package: @deepseek-ai/dsh-session-persistence-jsonl (`spec/dsh-session-persistence-jsonl/`)

- Backend guidelines: `.trellis/spec/dsh-session-persistence-jsonl/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-persistence-jsonl/frontend/`

### Package: @deepseek-ai/dsh-session-projection (`spec/dsh-session-projection/`)

- Backend guidelines: `.trellis/spec/dsh-session-projection/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-projection/frontend/`

### Package: @deepseek-ai/dsh-session-projection-cache (`spec/dsh-session-projection-cache/`)

- Backend guidelines: `.trellis/spec/dsh-session-projection-cache/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-projection-cache/frontend/`

### Package: @deepseek-ai/dsh-session-stats (`spec/dsh-session-stats/`)

- Backend guidelines: `.trellis/spec/dsh-session-stats/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-stats/frontend/`

### Package: @deepseek-ai/dsh-session-telemetry (`spec/dsh-session-telemetry/`)

- Backend guidelines: `.trellis/spec/dsh-session-telemetry/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-telemetry/frontend/`

### Package: @deepseek-ai/dsh-session-telemetry-otel (`spec/dsh-session-telemetry-otel/`)

- Backend guidelines: `.trellis/spec/dsh-session-telemetry-otel/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-telemetry-otel/frontend/`

### Package: @deepseek-ai/dsh-session-title (`spec/dsh-session-title/`)

- Backend guidelines: `.trellis/spec/dsh-session-title/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-title/frontend/`

### Package: @deepseek-ai/dsh-session-title-first-prompt-llm (`spec/dsh-session-title-first-prompt-llm/`)

- Backend guidelines: `.trellis/spec/dsh-session-title-first-prompt-llm/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-title-first-prompt-llm/frontend/`

### Package: @deepseek-ai/dsh-session-title-llm (`spec/dsh-session-title-llm/`)

- Backend guidelines: `.trellis/spec/dsh-session-title-llm/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-title-llm/frontend/`

### Package: @deepseek-ai/dsh-session-turn-outline (`spec/dsh-session-turn-outline/`)

- Backend guidelines: `.trellis/spec/dsh-session-turn-outline/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-turn-outline/frontend/`

### Package: @deepseek-ai/dsh-tool-working-directory (`spec/dsh-tool-working-directory/`)

- Backend guidelines: `.trellis/spec/dsh-tool-working-directory/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-working-directory/frontend/`

### Package: @deepseek-ai/dsh-working-directory (`spec/dsh-working-directory/`)

- Backend guidelines: `.trellis/spec/dsh-working-directory/backend/`

- Frontend guidelines: `.trellis/spec/dsh-working-directory/frontend/`

### Package: @deepseek-ai/dsh-session-log-export (`spec/dsh-session-log-export/`)

- Backend guidelines: `.trellis/spec/dsh-session-log-export/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-log-export/frontend/`

### Package: @deepseek-ai/dsh-session-query (`spec/dsh-session-query/`)

- Backend guidelines: `.trellis/spec/dsh-session-query/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-query/frontend/`

### Package: @deepseek-ai/dsh-session-query-sqlite (`spec/dsh-session-query-sqlite/`)

- Backend guidelines: `.trellis/spec/dsh-session-query-sqlite/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-query-sqlite/frontend/`

### Package: @deepseek-ai/dsh-settings (`spec/dsh-settings/`)

- Backend guidelines: `.trellis/spec/dsh-settings/backend/`

- Frontend guidelines: `.trellis/spec/dsh-settings/frontend/`

### Package: @deepseek-ai/dsh-bash-local (`spec/dsh-bash-local/`)

- Backend guidelines: `.trellis/spec/dsh-bash-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-bash-local/frontend/`

### Package: @deepseek-ai/dsh-bash-sandbox (`spec/dsh-bash-sandbox/`)

- Backend guidelines: `.trellis/spec/dsh-bash-sandbox/backend/`

- Frontend guidelines: `.trellis/spec/dsh-bash-sandbox/frontend/`

### Package: @deepseek-ai/dsh-pwsh-local (`spec/dsh-pwsh-local/`)

- Backend guidelines: `.trellis/spec/dsh-pwsh-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-pwsh-local/frontend/`

### Package: @deepseek-ai/dsh-pwsh-sandbox (`spec/dsh-pwsh-sandbox/`)

- Backend guidelines: `.trellis/spec/dsh-pwsh-sandbox/backend/`

- Frontend guidelines: `.trellis/spec/dsh-pwsh-sandbox/frontend/`

### Package: @deepseek-ai/dsh-shell (`spec/dsh-shell/`)

- Backend guidelines: `.trellis/spec/dsh-shell/backend/`

- Frontend guidelines: `.trellis/spec/dsh-shell/frontend/`

### Package: @deepseek-ai/dsh-shell-env (`spec/dsh-shell-env/`)

- Backend guidelines: `.trellis/spec/dsh-shell-env/backend/`

- Frontend guidelines: `.trellis/spec/dsh-shell-env/frontend/`

### Package: @deepseek-ai/dsh-tool-bash (`spec/dsh-tool-bash/`)

- Backend guidelines: `.trellis/spec/dsh-tool-bash/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-bash/frontend/`

### Package: @deepseek-ai/dsh-tool-bash-persistent (`spec/dsh-tool-bash-persistent/`)

- Backend guidelines: `.trellis/spec/dsh-tool-bash-persistent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-bash-persistent/frontend/`

### Package: @deepseek-ai/dsh-tool-pwsh (`spec/dsh-tool-pwsh/`)

- Backend guidelines: `.trellis/spec/dsh-tool-pwsh/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-pwsh/frontend/`

### Package: @deepseek-ai/dsh-tool-pwsh-persistent (`spec/dsh-tool-pwsh-persistent/`)

- Backend guidelines: `.trellis/spec/dsh-tool-pwsh-persistent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-pwsh-persistent/frontend/`

### Package: @deepseek-ai/dsh-skill (`spec/dsh-skill/`)

- Backend guidelines: `.trellis/spec/dsh-skill/backend/`

- Frontend guidelines: `.trellis/spec/dsh-skill/frontend/`

### Package: @deepseek-ai/dsh-skill-filesystem (`spec/dsh-skill-filesystem/`)

- Backend guidelines: `.trellis/spec/dsh-skill-filesystem/backend/`

- Frontend guidelines: `.trellis/spec/dsh-skill-filesystem/frontend/`

### Package: @deepseek-ai/dsh-skill-office (`spec/dsh-skill-office/`)

- Backend guidelines: `.trellis/spec/dsh-skill-office/backend/`

- Frontend guidelines: `.trellis/spec/dsh-skill-office/frontend/`

### Package: @deepseek-ai/dsh-tool-skill (`spec/dsh-tool-skill/`)

- Backend guidelines: `.trellis/spec/dsh-tool-skill/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-skill/frontend/`

### Package: @deepseek-ai/dsh-tool-workspace-dependencies (`spec/dsh-tool-workspace-dependencies/`)

- Backend guidelines: `.trellis/spec/dsh-tool-workspace-dependencies/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-workspace-dependencies/frontend/`

### Package: @deepseek-ai/dsh-spill (`spec/dsh-spill/`)

- Backend guidelines: `.trellis/spec/dsh-spill/backend/`

- Frontend guidelines: `.trellis/spec/dsh-spill/frontend/`

### Package: @deepseek-ai/dsh-spill-local (`spec/dsh-spill-local/`)

- Backend guidelines: `.trellis/spec/dsh-spill-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-spill-local/frontend/`

### Package: @deepseek-ai/dsh-spill-policy (`spec/dsh-spill-policy/`)

- Backend guidelines: `.trellis/spec/dsh-spill-policy/backend/`

- Frontend guidelines: `.trellis/spec/dsh-spill-policy/frontend/`

### Package: @deepseek-ai/dsh-fs-ssh (`spec/dsh-fs-ssh/`)

- Backend guidelines: `.trellis/spec/dsh-fs-ssh/backend/`

- Frontend guidelines: `.trellis/spec/dsh-fs-ssh/frontend/`

### Package: @deepseek-ai/dsh-sandbox-ssh (`spec/dsh-sandbox-ssh/`)

- Backend guidelines: `.trellis/spec/dsh-sandbox-ssh/backend/`

- Frontend guidelines: `.trellis/spec/dsh-sandbox-ssh/frontend/`

### Package: @deepseek-ai/dsh-ssh (`spec/dsh-ssh/`)

- Backend guidelines: `.trellis/spec/dsh-ssh/backend/`

- Frontend guidelines: `.trellis/spec/dsh-ssh/frontend/`

### Package: @deepseek-ai/dsh-ssh-helper-runtime (`spec/dsh-ssh-helper-runtime/`)

- Backend guidelines: `.trellis/spec/dsh-ssh-helper-runtime/backend/`

- Frontend guidelines: `.trellis/spec/dsh-ssh-helper-runtime/frontend/`

### Package: @deepseek-ai/dsh-subprocess-ssh (`spec/dsh-subprocess-ssh/`)

- Backend guidelines: `.trellis/spec/dsh-subprocess-ssh/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subprocess-ssh/frontend/`

### Package: @deepseek-ai/dsh-storage (`spec/dsh-storage/`)

- Backend guidelines: `.trellis/spec/dsh-storage/backend/`

- Frontend guidelines: `.trellis/spec/dsh-storage/frontend/`

### Package: @deepseek-ai/dsh-storage-domain (`spec/dsh-storage-domain/`)

- Backend guidelines: `.trellis/spec/dsh-storage-domain/backend/`

- Frontend guidelines: `.trellis/spec/dsh-storage-domain/frontend/`

### Package: @deepseek-ai/dsh-storage-json (`spec/dsh-storage-json/`)

- Backend guidelines: `.trellis/spec/dsh-storage-json/backend/`

- Frontend guidelines: `.trellis/spec/dsh-storage-json/frontend/`

### Package: @deepseek-ai/dsh-storage-sqlite (`spec/dsh-storage-sqlite/`)

- Backend guidelines: `.trellis/spec/dsh-storage-sqlite/backend/`

- Frontend guidelines: `.trellis/spec/dsh-storage-sqlite/frontend/`

### Package: @deepseek-ai/dsh-subagent (`spec/dsh-subagent/`)

- Backend guidelines: `.trellis/spec/dsh-subagent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent/frontend/`

### Package: @deepseek-ai/dsh-subagent-acp (`spec/dsh-subagent-acp/`)

- Backend guidelines: `.trellis/spec/dsh-subagent-acp/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent-acp/frontend/`

### Package: @deepseek-ai/dsh-subagent-claude-code (`spec/dsh-subagent-claude-code/`)

- Backend guidelines: `.trellis/spec/dsh-subagent-claude-code/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent-claude-code/frontend/`

### Package: @deepseek-ai/dsh-subagent-codex (`spec/dsh-subagent-codex/`)

- Backend guidelines: `.trellis/spec/dsh-subagent-codex/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent-codex/frontend/`

### Package: @deepseek-ai/dsh-subagent-dsh-sdk (`spec/dsh-subagent-dsh-sdk/`)

- Backend guidelines: `.trellis/spec/dsh-subagent-dsh-sdk/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent-dsh-sdk/frontend/`

### Package: @deepseek-ai/dsh-subagent-fork-in-process (`spec/dsh-subagent-fork-in-process/`)

- Backend guidelines: `.trellis/spec/dsh-subagent-fork-in-process/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent-fork-in-process/frontend/`

### Package: @deepseek-ai/dsh-subagent-spawn-in-process (`spec/dsh-subagent-spawn-in-process/`)

- Backend guidelines: `.trellis/spec/dsh-subagent-spawn-in-process/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subagent-spawn-in-process/frontend/`

### Package: @deepseek-ai/dsh-tool-subagent (`spec/dsh-tool-subagent/`)

- Backend guidelines: `.trellis/spec/dsh-tool-subagent/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-subagent/frontend/`

### Package: @deepseek-ai/dsh-tool-subagent-control (`spec/dsh-tool-subagent-control/`)

- Backend guidelines: `.trellis/spec/dsh-tool-subagent-control/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-subagent-control/frontend/`

### Package: @deepseek-ai/dsh-subprocess (`spec/dsh-subprocess/`)

- Backend guidelines: `.trellis/spec/dsh-subprocess/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subprocess/frontend/`

### Package: @deepseek-ai/dsh-subprocess-local (`spec/dsh-subprocess-local/`)

- Backend guidelines: `.trellis/spec/dsh-subprocess-local/backend/`

- Frontend guidelines: `.trellis/spec/dsh-subprocess-local/frontend/`

### Package: @deepseek-ai/dsh-win32-process (`spec/dsh-win32-process/`)

- Backend guidelines: `.trellis/spec/dsh-win32-process/backend/`

- Frontend guidelines: `.trellis/spec/dsh-win32-process/frontend/`

### Package: @deepseek-ai/dsh-agent-team (`spec/dsh-agent-team/`)

- Backend guidelines: `.trellis/spec/dsh-agent-team/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-team/frontend/`

### Package: @deepseek-ai/dsh-tool-agent-team (`spec/dsh-tool-agent-team/`)

- Backend guidelines: `.trellis/spec/dsh-tool-agent-team/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-agent-team/frontend/`

### Package: @deepseek-ai/dsh-otel (`spec/dsh-otel/`)

- Backend guidelines: `.trellis/spec/dsh-otel/backend/`

- Frontend guidelines: `.trellis/spec/dsh-otel/frontend/`

### Package: @deepseek-ai/dsh-terminal (`spec/dsh-terminal/`)

- Backend guidelines: `.trellis/spec/dsh-terminal/backend/`

- Frontend guidelines: `.trellis/spec/dsh-terminal/frontend/`

### Package: @deepseek-ai/dsh-terminal-bash (`spec/dsh-terminal-bash/`)

- Backend guidelines: `.trellis/spec/dsh-terminal-bash/backend/`

- Frontend guidelines: `.trellis/spec/dsh-terminal-bash/frontend/`

### Package: @deepseek-ai/dsh-agent-loop-testkit (`spec/dsh-agent-loop-testkit/`)

- Backend guidelines: `.trellis/spec/dsh-agent-loop-testkit/backend/`

- Frontend guidelines: `.trellis/spec/dsh-agent-loop-testkit/frontend/`

### Package: @deepseek-ai/dsh-client-test-runtime (`spec/dsh-client-test-runtime/`)

- Backend guidelines: `.trellis/spec/dsh-client-test-runtime/backend/`

- Frontend guidelines: `.trellis/spec/dsh-client-test-runtime/frontend/`

### Package: @deepseek-ai/dsh-llm-mock-server (`spec/dsh-llm-mock-server/`)

- Backend guidelines: `.trellis/spec/dsh-llm-mock-server/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-mock-server/frontend/`

### Package: @deepseek-ai/dsh-llm-replay (`spec/dsh-llm-replay/`)

- Backend guidelines: `.trellis/spec/dsh-llm-replay/backend/`

- Frontend guidelines: `.trellis/spec/dsh-llm-replay/frontend/`

### Package: @deepseek-ai/dsh-loader-smoke (`spec/dsh-loader-smoke/`)

- Backend guidelines: `.trellis/spec/dsh-loader-smoke/backend/`

- Frontend guidelines: `.trellis/spec/dsh-loader-smoke/frontend/`

### Package: @deepseek-ai/dsh-remote-mock (`spec/dsh-remote-mock/`)

- Backend guidelines: `.trellis/spec/dsh-remote-mock/backend/`

- Frontend guidelines: `.trellis/spec/dsh-remote-mock/frontend/`

### Package: @deepseek-ai/dsh-session-snapshot (`spec/dsh-session-snapshot/`)

- Backend guidelines: `.trellis/spec/dsh-session-snapshot/backend/`

- Frontend guidelines: `.trellis/spec/dsh-session-snapshot/frontend/`

### Package: @deepseek-ai/dsh-tool-testkit (`spec/dsh-tool-testkit/`)

- Backend guidelines: `.trellis/spec/dsh-tool-testkit/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-testkit/frontend/`

### Package: @deepseek-ai/dsh-tool-todo (`spec/dsh-tool-todo/`)

- Backend guidelines: `.trellis/spec/dsh-tool-todo/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-todo/frontend/`

### Package: @deepseek-ai/dsh-typert-generator (`spec/dsh-typert-generator/`)

- Backend guidelines: `.trellis/spec/dsh-typert-generator/backend/`

- Frontend guidelines: `.trellis/spec/dsh-typert-generator/frontend/`

### Package: @deepseek-ai/dsh-typert-loader (`spec/dsh-typert-loader/`)

- Backend guidelines: `.trellis/spec/dsh-typert-loader/backend/`

- Frontend guidelines: `.trellis/spec/dsh-typert-loader/frontend/`

### Package: @deepseek-ai/dsh-typert-protocol (`spec/dsh-typert-protocol/`)

- Backend guidelines: `.trellis/spec/dsh-typert-protocol/backend/`

- Frontend guidelines: `.trellis/spec/dsh-typert-protocol/frontend/`

### Package: @deepseek-ai/dsh-typert-registry (`spec/dsh-typert-registry/`)

- Backend guidelines: `.trellis/spec/dsh-typert-registry/backend/`

- Frontend guidelines: `.trellis/spec/dsh-typert-registry/frontend/`

### Package: @deepseek-ai/dsh-atomic-write (`spec/dsh-atomic-write/`)

- Backend guidelines: `.trellis/spec/dsh-atomic-write/backend/`

- Frontend guidelines: `.trellis/spec/dsh-atomic-write/frontend/`

### Package: @deepseek-ai/dsh-brand (`spec/dsh-brand/`)

- Backend guidelines: `.trellis/spec/dsh-brand/backend/`

- Frontend guidelines: `.trellis/spec/dsh-brand/frontend/`

### Package: @deepseek-ai/dsh-chunked-list (`spec/dsh-chunked-list/`)

- Backend guidelines: `.trellis/spec/dsh-chunked-list/backend/`

- Frontend guidelines: `.trellis/spec/dsh-chunked-list/frontend/`

### Package: @deepseek-ai/dsh-util-code-language (`spec/dsh-util-code-language/`)

- Backend guidelines: `.trellis/spec/dsh-util-code-language/backend/`

- Frontend guidelines: `.trellis/spec/dsh-util-code-language/frontend/`

### Package: @deepseek-ai/dsh-util-crypto (`spec/dsh-util-crypto/`)

- Backend guidelines: `.trellis/spec/dsh-util-crypto/backend/`

- Frontend guidelines: `.trellis/spec/dsh-util-crypto/frontend/`

### Package: @deepseek-ai/dsh-deque (`spec/dsh-deque/`)

- Backend guidelines: `.trellis/spec/dsh-deque/backend/`

- Frontend guidelines: `.trellis/spec/dsh-deque/frontend/`

### Package: @deepseek-ai/dsh-util-file-drag (`spec/dsh-util-file-drag/`)

- Backend guidelines: `.trellis/spec/dsh-util-file-drag/backend/`

- Frontend guidelines: `.trellis/spec/dsh-util-file-drag/frontend/`

### Package: @deepseek-ai/dsh-home-paths (`spec/dsh-home-paths/`)

- Backend guidelines: `.trellis/spec/dsh-home-paths/backend/`

- Frontend guidelines: `.trellis/spec/dsh-home-paths/frontend/`

### Package: @deepseek-ai/dsh-http-proxy (`spec/dsh-http-proxy/`)

- Backend guidelines: `.trellis/spec/dsh-http-proxy/backend/`

- Frontend guidelines: `.trellis/spec/dsh-http-proxy/frontend/`

### Package: @deepseek-ai/dsh-launch-environment (`spec/dsh-launch-environment/`)

- Backend guidelines: `.trellis/spec/dsh-launch-environment/backend/`

- Frontend guidelines: `.trellis/spec/dsh-launch-environment/frontend/`

### Package: @deepseek-ai/dsh-lazy-require (`spec/dsh-lazy-require/`)

- Backend guidelines: `.trellis/spec/dsh-lazy-require/backend/`

- Frontend guidelines: `.trellis/spec/dsh-lazy-require/frontend/`

### Package: @deepseek-ai/dsh-native-command (`spec/dsh-native-command/`)

- Backend guidelines: `.trellis/spec/dsh-native-command/backend/`

- Frontend guidelines: `.trellis/spec/dsh-native-command/frontend/`

### Package: @deepseek-ai/dsh-official-bundles (`spec/dsh-official-bundles/`)

- Backend guidelines: `.trellis/spec/dsh-official-bundles/backend/`

- Frontend guidelines: `.trellis/spec/dsh-official-bundles/frontend/`

### Package: @deepseek-ai/dsh-output-retention (`spec/dsh-output-retention/`)

- Backend guidelines: `.trellis/spec/dsh-output-retention/backend/`

- Frontend guidelines: `.trellis/spec/dsh-output-retention/frontend/`

### Package: @deepseek-ai/dsh-package-manifest (`spec/dsh-package-manifest/`)

- Backend guidelines: `.trellis/spec/dsh-package-manifest/backend/`

- Frontend guidelines: `.trellis/spec/dsh-package-manifest/frontend/`

### Package: @deepseek-ai/dsh-plugin-detail (`spec/dsh-plugin-detail/`)

- Backend guidelines: `.trellis/spec/dsh-plugin-detail/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plugin-detail/frontend/`

### Package: @deepseek-ai/dsh-plugin-market-index (`spec/dsh-plugin-market-index/`)

- Backend guidelines: `.trellis/spec/dsh-plugin-market-index/backend/`

- Frontend guidelines: `.trellis/spec/dsh-plugin-market-index/frontend/`

### Package: @deepseek-ai/dsh-util-time (`spec/dsh-util-time/`)

- Backend guidelines: `.trellis/spec/dsh-util-time/backend/`

- Frontend guidelines: `.trellis/spec/dsh-util-time/frontend/`

### Package: @deepseek-ai/dsh-timeout (`spec/dsh-timeout/`)

- Backend guidelines: `.trellis/spec/dsh-timeout/backend/`

- Frontend guidelines: `.trellis/spec/dsh-timeout/frontend/`

### Package: @deepseek-ai/dsh-util-values (`spec/dsh-util-values/`)

- Backend guidelines: `.trellis/spec/dsh-util-values/backend/`

- Frontend guidelines: `.trellis/spec/dsh-util-values/frontend/`

### Package: @deepseek-ai/dsh-util-workspace-path (`spec/dsh-util-workspace-path/`)

- Backend guidelines: `.trellis/spec/dsh-util-workspace-path/backend/`

- Frontend guidelines: `.trellis/spec/dsh-util-workspace-path/frontend/`

### Package: @deepseek-ai/dsh-tool-web (`spec/dsh-tool-web/`)

- Backend guidelines: `.trellis/spec/dsh-tool-web/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-web/frontend/`

### Package: @deepseek-ai/dsh-web (`spec/dsh-web/`)

- Backend guidelines: `.trellis/spec/dsh-web/backend/`

- Frontend guidelines: `.trellis/spec/dsh-web/frontend/`

### Package: @deepseek-ai/dsh-web-deepseek-api (`spec/dsh-web-deepseek-api/`)

- Backend guidelines: `.trellis/spec/dsh-web-deepseek-api/backend/`

- Frontend guidelines: `.trellis/spec/dsh-web-deepseek-api/frontend/`

### Package: @deepseek-ai/dsh-web-fetch-http (`spec/dsh-web-fetch-http/`)

- Backend guidelines: `.trellis/spec/dsh-web-fetch-http/backend/`

- Frontend guidelines: `.trellis/spec/dsh-web-fetch-http/frontend/`

### Package: @deepseek-ai/dsh-web-search-deepseek (`spec/dsh-web-search-deepseek/`)

- Backend guidelines: `.trellis/spec/dsh-web-search-deepseek/backend/`

- Frontend guidelines: `.trellis/spec/dsh-web-search-deepseek/frontend/`

### Package: @deepseek-ai/dsh-tool-workflow (`spec/dsh-tool-workflow/`)

- Backend guidelines: `.trellis/spec/dsh-tool-workflow/backend/`

- Frontend guidelines: `.trellis/spec/dsh-tool-workflow/frontend/`

### Package: @deepseek-ai/dsh-workflow (`spec/dsh-workflow/`)

- Backend guidelines: `.trellis/spec/dsh-workflow/backend/`

- Frontend guidelines: `.trellis/spec/dsh-workflow/frontend/`

### Package: @deepseek-ai/dsh-workflow-ptc (`spec/dsh-workflow-ptc/`)

- Backend guidelines: `.trellis/spec/dsh-workflow-ptc/backend/`

- Frontend guidelines: `.trellis/spec/dsh-workflow-ptc/frontend/`

### Package: @deepseek-ai/dsh-workspace (`spec/dsh-workspace/`)

- Backend guidelines: `.trellis/spec/dsh-workspace/backend/`

- Frontend guidelines: `.trellis/spec/dsh-workspace/frontend/`

### Package: @deepseek-ai/node-addon-system-workspace (`spec/node-addon-system-workspace/`)

- Frontend guidelines: `.trellis/spec/node-addon-system-workspace/frontend/`

### Package: @deepseek-ai/node-addon-system-darwin-arm64 (`spec/node-addon-system-darwin-arm64/`)

- Frontend guidelines: `.trellis/spec/node-addon-system-darwin-arm64/frontend/`

### Package: @deepseek-ai/node-addon-system-darwin-x64 (`spec/node-addon-system-darwin-x64/`)

- Frontend guidelines: `.trellis/spec/node-addon-system-darwin-x64/frontend/`

### Package: @deepseek-ai/node-addon-system (`spec/node-addon-system/`)

- Backend guidelines: `.trellis/spec/node-addon-system/backend/`

- Frontend guidelines: `.trellis/spec/node-addon-system/frontend/`

### Package: @deepseek-ai/node-addon-system-linux-arm64 (`spec/node-addon-system-linux-arm64/`)

- Frontend guidelines: `.trellis/spec/node-addon-system-linux-arm64/frontend/`

### Package: @deepseek-ai/node-addon-system-linux-x64 (`spec/node-addon-system-linux-x64/`)

- Frontend guidelines: `.trellis/spec/node-addon-system-linux-x64/frontend/`

### Package: @deepseek-ai/dsh (`spec/dsh/`)

- Frontend guidelines: `.trellis/spec/dsh/frontend/`

### Package: @deepseek-ai/dsh-desktop (`spec/dsh-desktop/`)

- Frontend guidelines: `.trellis/spec/dsh-desktop/frontend/`

### Package: @deepseek-ai/dsh-desktop-host (`spec/dsh-desktop-host/`)

- Backend guidelines: `.trellis/spec/dsh-desktop-host/backend/`

- Frontend guidelines: `.trellis/spec/dsh-desktop-host/frontend/`

### Package: @deepseek-ai/dsh-plugin-market-generator (`spec/dsh-plugin-market-generator/`)

- Frontend guidelines: `.trellis/spec/dsh-plugin-market-generator/frontend/`

### Package: @deepseek-ai/dsh-web-frontend (`spec/dsh-web-frontend/`)

- Frontend guidelines: `.trellis/spec/dsh-web-frontend/frontend/`

### Package: @deepseek-ai/dsh-benchmarks (`spec/dsh-benchmarks/`)

- Frontend guidelines: `.trellis/spec/dsh-benchmarks/frontend/`

### Package: @deepseek-ai/website (`spec/website/`)

- Frontend guidelines: `.trellis/spec/website/frontend/`

### Package: dsh-python-runtime-closure (`spec/dsh-python-runtime-closure/`)

- Backend guidelines: `.trellis/spec/dsh-python-runtime-closure/backend/`

- Frontend guidelines: `.trellis/spec/dsh-python-runtime-closure/frontend/`


### Thinking guides (already populated)

`.trellis/spec/guides/` contains general thinking guides pre-filled with
best practices. Customize only if something clearly doesn't fit this project.

---

## How to fill the spec

### Step 1: Import from existing convention files first (preferred)

Search the repo for existing convention docs. If any exist, read them and
extract the relevant rules into the matching `.trellis/spec/` files —
usually much faster than documenting from scratch.

| File / Directory | Tool |
|------|------|
| `CLAUDE.md` / `CLAUDE.local.md` | Claude Code |
| `AGENTS.md` | Codex / Claude Code / agent-compatible tools |
| `.cursorrules` | Cursor |
| `.cursor/rules/*.mdc` | Cursor (rules directory) |
| `.windsurfrules` | Windsurf |
| `.clinerules` | Cline |
| `.roomodes` | Roo Code |
| `.github/copilot-instructions.md` | GitHub Copilot |
| `.vscode/settings.json` → `github.copilot.chat.codeGeneration.instructions` | VS Code Copilot |
| `CONVENTIONS.md` / `.aider.conf.yml` | aider |
| `CONTRIBUTING.md` | General project conventions |
| `.editorconfig` | Editor formatting rules |

### Step 2: Analyze the codebase for anything not covered by existing docs

Scan real code to discover patterns. Before writing each spec file:
- Find 2-3 real examples of each pattern in the codebase.
- Reference real file paths (not hypothetical ones).
- Document anti-patterns the team clearly avoids.

### Step 3: Document reality, not ideals

**Critical**: write what the code *actually does*, not what it should do.
Sub-agents match the spec, so aspirational patterns that don't exist in the
codebase will cause sub-agents to write code that looks out of place.

If the team has known tech debt, document the current state — improvement
is a separate conversation, not a bootstrap concern.

---

## Quick explainer of the runtime (share when they ask "why do we need spec at all")

- Every AI coding task spawns two sub-agents: `trellis-implement` (writes
  code) and `trellis-check` (verifies quality).
- Each task has `implement.jsonl` / `check.jsonl` manifests listing which
  spec files to load.
- The platform hook auto-injects those spec files + the task's `prd.md`
  into every sub-agent prompt, so the sub-agent codes/reviews per team
  conventions without anyone pasting them manually.
- Source of truth: `.trellis/spec/`. That's why filling it well now pays
  off forever.

---

## Completion

When the developer confirms the checklist items above are done with real
examples (not placeholders), guide them to run:

```bash
python3 ./.trellis/scripts/task.py finish
python3 ./.trellis/scripts/task.py archive 00-bootstrap-guidelines
```

After archive, every new developer who joins this project will get a
`00-join-<slug>` onboarding task instead of this bootstrap task.

---

## Suggested opening line

"Welcome to Trellis! Your init just set me up to help you fill the project
spec — a one-time setup so every future AI session follows the team's
conventions instead of writing generic code. Before we start, do you have
any existing convention docs (CLAUDE.md, .cursorrules, CONTRIBUTING.md,
etc.) I can pull from, or should I scan the codebase from scratch?"
