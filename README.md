# anonim-chat
private void getUpdates(final TelegramBot bot) {         try {             GetUpdatesResponse response = bot.execute(                     new GetUpdates()                             .limit(LIMIT)                             .offset(updateId.get())                             .timeout(LONG_POLLING_TIMEOUT));              if (response != null &amp;&amp; response.updates() != null &amp;&amp; response.updates().size() > 0) {                 for (Update update : response.updates()) {                     obtainUpdate(bot, update);                     updateId.set(update.updateId() + 1);                 }             }         } catch (Exception e) {             ErrorUtils.log(TAG, e);         }     }
