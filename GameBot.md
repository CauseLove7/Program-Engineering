# Тема Мой проект
### Отчет по проекту подготовил:
- Козлов Максим Игоревич
- ПИЭ-21-2

| Задание | Лаб. раб. | Сам. раб. |
| ------ | ------ | ------ |
| Проект | - | + |

Работу проверили:
- к.э.н., доцент Панов М.А.
- import telebot
from telebot import types

bot = telebot.TeleBot('6844637210:AAGMoWTfB6Klrb2Bh8n28irD0a-m80wNVEg')

@bot.message_handler(commands=['start'])
def start(message):
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    start_button = types.KeyboardButton('/start')
    help_button = types.KeyboardButton('/help')
    info_button = types.KeyboardButton('/info')

    markup.add(start_button, help_button, info_button)

    bot.send_message(message.chat.id, 'Привет! Я GameBot - тест-бот для рекомендации игр!', reply_markup=markup)

@bot.message_handler(commands=['help'])
def help(message):
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    start_button = types.KeyboardButton('/start')
    help_button = types.KeyboardButton('/help')
    info_button = types.KeyboardButton('/info')

    markup.add(start_button, help_button, info_button)

    bot.send_message(message.chat.id, 'Конечно, я готов вам помочь! Что вас интересует?', reply_markup=markup)

@bot.message_handler(commands=['info'])
def get_user_info(message):
    show_categories(message.chat.id)
@bot.callback_query_handler(func=lambda call: call.data == "show_categories")
def show_categories(chat_id):
    markup = types.InlineKeyboardMarkup(row_width=1)
    strategy = types.InlineKeyboardButton(text="Стратегии", callback_data="category_strategy")
    horror = types.InlineKeyboardButton(text="Ужасы", callback_data="category_horror")
    sport = types.InlineKeyboardButton(text="Спортивные симуляторы", callback_data="category_sport")
    reset_button = types.InlineKeyboardButton(text="Сбросить переписку", callback_data="reset_chat")

    markup.add(strategy, horror, sport, reset_button)

    bot.send_message(chat_id, "Выберите категорию:", reply_markup=markup)

@bot.callback_query_handler(func=lambda call: call.data.startswith("category"))
def show_games_in_category(call):
    category = call.data.replace("category_", "")

    if category == "strategy":
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True, one_time_keyboard=True)
        bot.send_message(call.message.chat.id, "Вот некоторые стратегии:")
        games = [
            "Expeditions: Rome - https://store.steampowered.com/app/987840/Expeditions_Rome/",
            "Total War: Warhammer 3 - https://store.steampowered.com/app/1142710/Total_War_WARHAMMER_III/",
            "IXION - https://store.steampowered.com/app/1113120/IXION/",
            "Frozenheim - https://store.steampowered.com/app/1134100/Frozenheim/",
            "Hearts of Iron IV - https://store.steampowered.com/app/394360/Hearts_of_Iron_IV/",
            "Sid Meier’s Civilization VI - https://store.steampowered.com/app/289070/Sid_Meiers_Civilization_VI/",
            "Victoria 3 - https://store.steampowered.com/app/529340/Victoria_3/"
        ]

        for game in games:
            markup.add(types.KeyboardButton(game))

        back_button = types.KeyboardButton("Назад к категориям")
        markup.add(back_button)

        bot.send_message(call.message.chat.id, "Выберите игру:", reply_markup=markup)

    elif category == "horror":
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True, one_time_keyboard=True)
        bot.send_message(call.message.chat.id, "Хууууу,давно не было мурашек?Вот вам подборочка страшилок!")

        horror_games = [
            "Dead Space 2023 - https://store.steampowered.com/app/1693980/Dead_Space/",
            "Resident Evil 4 (2023) - https://store.steampowered.com/app/2050650/Resident_Evil_4/",
            "Phasmophobia - https://store.steampowered.com/app/739630/Phasmophobia/",
            "Demonologist - https://store.steampowered.com/app/1929610/Demonologist/",
            "Tiny Bunny - https://store.steampowered.com/app/1421250/Tiny_Bunny/",
        ]

        for horror_game in horror_games:
            markup.add(types.KeyboardButton(horror_game))

        back_button = types.KeyboardButton("Назад к категориям")
        markup.add(back_button)

        bot.send_message(call.message.chat.id, "Выберите игру:", reply_markup=markup)

    elif category == "sport":
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True, one_time_keyboard=True)
        bot.send_message(call.message.chat.id, "Соскучились по спорту? Вот небольшой список для вас :)")
       
        sport_games=[
            "EA Sports FC 24 - https://store.steampowered.com/app/2195250/EA_SPORTS_FC_24/",
            "F1 23 - https://store.steampowered.com/app/2108330/F1_23/",
            "WWE 2K23 - https://store.steampowered.com/app/1942660/WWE_2K23/",
            "Football Manager 2024 - https://store.steampowered.com/app/2252570/Football_Manager_2024/",
            "NBA 2K24 - https://store.steampowered.com/app/2338770/NBA_2K24/",
        ]
        for sport_game in sport_games:
            markup.add(types.KeyboardButton(sport_game))

        back_button = types.KeyboardButton("Назад к категориям")
        markup.add(back_button)

        bot.send_message(call.message.chat.id, "Выберите игру:", reply_markup=markup)

@bot.message_handler(func=lambda message: message.text == "Назад к категориям")
def back_to_categories(message):
    show_categories(message.chat.id)

@bot.callback_query_handler(func=lambda call: call.data == "reset_chat")
def reset_chat(call):
    bot.send_message(call.message.chat.id, "Переписка сброшена. Начните заново с команды /start")

bot.polling(none_stop=True)
#### Результат:
