---
title: Flaric Admins
---
# Intro

Here let me list out the overall plans about how the new admin panel will be distributed.

## 👑 Founder
Founder is the group creator, with all the power from telegram and from the Bot
➕ Appears first in the Staff list
➕ They can manage cofounders, moderators, helper, free users
➕ They can manage all the users, also admins

> Founder can be changed, directly with Telegram system.

## ⚜ Co-Founder
They are Admins with extra power
➕ They appear in the Staff list
➕ They can set cofounders, moderators, helper, free users and they can ban them

> Commands: /cofounder and /uncofounder

## 👮 Admin
➕ They appear in Staff list
➕ They can manage group /settings
➕ They can moderate users (from Telegram o with commands like /ban), if they have "Ban users" permission
➕ They can delete messages (from Telegram o with /del and /logdel), if they have "Delete messages" permission
➕ They can manage pinned messages (from Telegram o with commands like /pin), if they have "Pin messages" permission

> There are 2 ways to add/remove them:
• using the commands /admin and /unadmin
• setting them from the administrators panel of the Telegram group and then using /reload in the group

## 👷🏻‍♂️ Moderator
➕ They appear in the Staff list
➕ They can use all moderation commands from the bot (ban, kick, unban, info, infopvt, mute, unmute)
➕ They are free users
➖ They cannot delete messages

> Commands: /mod and /unmod

## 🛃 Chat Cleaner
➕ They appear in the Staff list
➕ They can delete messages with /del or /logdel
➖ They cannot moderate users
➖ They aren't free by default

> Commands: /cleaner and /uncleaner

## 🙊 Muter
➕ They can mute and unmute users with bot commands
➕ They are free users
➖ They cannot ban/unban/kick users
➖ They cannot delete messages

> Commands: /muter and /unmuter

## ⛑ Helper
➕ They appear in Staff list
➖ They don't have any power
➖ They aren't free users

> Commands: /helper and /unhelper

## 🔓 Free
➕ The Bot ignores them for automatic punishment like antispam, antiflood, media block, global silence...

> Commands: /free and /unfree