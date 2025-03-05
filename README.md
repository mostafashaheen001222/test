import telegram
    from telegram.ext import Updater, MessageHandler, Filters

    TOKEN = '7552398957:AAEAF6-cI9HFaNt3Q27uZbKEuQ5Ia1V_5y8'  # توكن البوت
    CHANNEL_ID = -1002357833167  # معرف القناة
    GROUP_ID = -1002485821765  # معرف المجموعة

    def handle_channel_post(update, context):
        if update.channel_post:
            context.bot.copy_message(chat_id=GROUP_ID, from_chat_id=CHANNEL_ID, message_id=update.channel_post.message_id)

    def main():
        updater = Updater(TOKEN, use_context=True)
        dp = updater.dispatcher
        dp.add_handler(MessageHandler(Filters.channel_posts, handle_channel_post))
        updater.start_polling()
        updater.idle()

    if __name__ == '__main__':
        main()
