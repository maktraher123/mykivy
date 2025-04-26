from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
from kivy.uix.label import Label

# Кастомный алфавит
custom_to_russian = {
    "1.": "А", "2.": "Б", "3.": "В", "4.": "Г", "5.": "Д", "6.": "Е", "7.": "Ё", "8.": "Ж", "9.": "З", "10.": "И",
    "01.": "Й", "02.": "К", "03.": "Л", "04.": "М", "05.": "Н", "06.": "О", "07.": "П", "08.": "Р", "09.": "С",
    "010.": "Т", "001.": "У", "002.": "Ф", "003.": "Х", "004.": "Ц", "005.": "Ч", "006.": "Ш", "007.": "Щ",
    "008.": "Ъ", "009.": "Ь", "0010.": "Э", "0.": "Ю", "00.": "Я", "000.": "Ы"
}
russian_to_custom = {v: k for k, v in custom_to_russian.items()}

def decrypt(text):
    result = ""
    buffer = ""
    i = 0
    while i < len(text):
        buffer += text[i]
        i += 1
        if buffer.endswith('.'):
            result += custom_to_russian.get(buffer, '?')
            buffer = ""
    return result

def encrypt(text):
    result = ""
    for char in text.upper():
        result += russian_to_custom.get(char, '?')
    return result

class DecoderApp(App):
    def build(self):
        layout = BoxLayout(orientation='vertical', padding=10, spacing=10)

        self.input_text = TextInput(hint_text='Введи текст (шифр или русский)', multiline=True, size_hint_y=0.3)
        layout.add_widget(self.input_text)

        self.result_label = Label(text='Результат появится здесь', size_hint_y=0.3)
        layout.add_widget(self.result_label)

        btn_decrypt = Button(text='Расшифровать (-> Русский)')
        btn_decrypt.bind(on_press=self.on_decrypt)
        layout.add_widget(btn_decrypt)

        btn_encrypt = Button(text='Зашифровать (-> Кастомный)')
        btn_encrypt.bind(on_press=self.on_encrypt)
        layout.add_widget(btn_encrypt)

        return layout

    def on_decrypt(self, instance):
        text = self.input_text.text
        result = decrypt(text)
        self.result_label.text = result

    def on_encrypt(self, instance):
        text = self.input_text.text
        result = encrypt(text)
        self.result_label.text = result

if __name__ == '__main__':
    DecoderApp().run()
