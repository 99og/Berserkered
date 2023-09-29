<br/>
<p align="center">
  <a href="https://media.discordapp.net/attachments/1102599085216759839/1157396593469825105/Surtr.jpg?ex=65187513&is=65172393&hm=51db33512f9e8e1c9f547598993bea92ea391ded64a72b74a265326408cb0dbe&=&width=503&height=671">
    <img src="https://media.discordapp.net/attachments/1102599085216759839/1157396593469825105/Surtr.jpg?ex=65187513&is=65172393&hm=51db33512f9e8e1c9f547598993bea92ea391ded64a72b74a265326408cb0dbe&=&width=503&height=671" alt="Logo" width=400 ></a>
  <h3 align="center">🌋Berserkered Deobfuscator 🌋</h3>
  <p align="center">
    One Of the Greatest and Hardest way to Deobfuscate the Berserker Wall !

</p>







---
## Preview of [Berserkered]() :
```python3
from pystyle import *
import sys
import os
import time


__author__ = '.zqh aka zqh#0684'

# Credits to billythegoat356 who made the obfuscsator -> https://github.com/billythegoat356/Berserker


class Berserkered:

    '''
    Deobfuscation of Berserker wall
    Issues -> caracteres 
    '''

    def __init__(self) -> None:

        self.attributes = ["_eval", "_exec", "_byte", "_bytes", "_bit", "_bits",
                           "_system", "_encode", "_decode", "_delete", "_exit", "_rasputin", "_boom", "_sparkle"]

        self.separate = ['~', '|', '-', '/', '=']
        self.spacejump = ['¤', '§', '^', '*', '¨']
        self.initvars = "abcdefghijklmnopqrstuvwxyz0123456789"

        self.fix = [0x0, 0x1, 0x28, 0x4A, '\n']  # dont touch this

        self.path = Write.Input(
            ' [?] Drag the file you want to Berserkered -> ', Colors.purple_to_red, interval=0.005)

        with open(self.path, 'r') as f:

            self.content = str(f.read())

    def format(self):
        '''
        format the berserker main code, replacing self attributes by their values
        Many issues ...
        '''

        for chars in range(len(self.attributes)):
            if f'self.{self.attributes[chars]}[' in self.content:
                for stacks in range(self.fix[2], self.fix[2]):
                    if f"self.{self.attributes[chars]}[{stacks}]" in self.content:
                        frm = f"self.{self.attributes[chars]}[{stacks}]"
                        self.content = self.content.replace(
                            frm, self.initvars[stacks])
        Write.Print(f''' [+] Formating the File \n''',
                    Colors.purple_to_red, interval=0.005)

    def getkey(self):  # find the key used in the file

        if "ord(t)-" in self.content:
            b = self.content.find('''ord(t)-''')
            c = b+30
            v = self.content[b:c]
            key = ""
            for c in v:
                if c.isdigit():
                    key += str(c)
                    self.key = int(key)
                # return self.key
            Write.Print(
                f''' [!] Key {self.key} used in the file \n''', Colors.purple_to_red, interval=0.005)

    def Unsparkled(self):

        if f"{self.attributes[13]}='''" in self.content:
            _sparkle_ = str(self.content[self.content.find(
                f'''{self.attributes[13]}=''')+12:-4])
            for delimiter in _sparkle_:
                if delimiter in self.separate:
                    cmpsr = delimiter
            for spacejumping in _sparkle_:
                if spacejumping in self.spacejump:
                    space = spacejumping
            stack, self.decrypted = [], []
            for sprkl in range(len(_sparkle_)):
                if _sparkle_[sprkl].isdigit():
                    stack += _sparkle_[sprkl]
                elif _sparkle_[sprkl] == cmpsr:
                    self.decrypted.append(''.join(map(str, stack)))
                    stack = []
                elif space in _sparkle_[sprkl]:
                    stack += [self.fix[4]]
        else:
            Write.Input(f''' [!] Your File is not obfuscated with Berserker, Please retry \n''',
                        Colors.purple_to_red, interval=0.005)
            sys.exit()
        self.decrypted.append(''.join(map(str, stack)))
        Write.Print(
            f''' [!] Len of sparkle wall -> {len(self.decrypted)}  \n''', Colors.purple_to_red, interval=0.005)
        Write.Print(f''' [+] Unsparkling The wall  \n''',
                    Colors.purple_to_red, interval=0.005)
        Write.Print(f''' [!] Space jumping : '{space}' \n''',
                    Colors.purple_to_red, interval=0.005)
        # return self.decrypted

    def decrypt_final_ouptut(self):
        final_code = ''
        for sparkle_l in self.decrypted:
            if sparkle_l.isdigit():
                if chr(int(sparkle_l)-self.key-len(self.decrypted)+self.fix[1]) in self.initvars:
                    final_code += chr(int(sparkle_l)-self.key -
                                      len(self.decrypted)+self.fix[1])
                elif chr(int(sparkle_l)-self.key-len(self.decrypted)+self.fix[2]) == self.initvars[0]:
                    final_code += chr(int(sparkle_l)-self.key -
                                      len(self.decrypted)+self.fix[2])
                elif chr(int(sparkle_l)-self.key-len(self.decrypted)) == "z":
                    if chr(int(sparkle_l)-self.key-len(self.decrypted)-self.fix[3]) == "0":
                        final_code += chr(int(sparkle_l)-self.key -
                                          len(self.decrypted)-self.fix[3])
                    else:
                        final_code += chr(int(sparkle_l) -
                                          self.key-len(self.decrypted))
                else:
                    final_code += chr(int(sparkle_l) -
                                      self.key-len(self.decrypted))
            if sparkle_l == self.fix[4]:
                final_code += sparkle_l
        bsrk = open(
            f'{os.path.splitext(os.path.basename(self.path))[0]}-deobf.py', 'w', encoding='utf-8')
        bsrk.write("""#                                                     [-----------------------------------------------------------------]\n#                                                     [ ~ This file has been deobfuscated by Berserkered made by .zqh ~ ]\n#                                                     [ ~  Credits to billythegoat356 who made Berserker Obfuscator   ~ ]\n#                                                     [ ~              My github -> github.com/99og                   ~ ]\n#                                                     [-----------------------------------------------------------------]\n\n\n""")
        bsrk.write(str(final_code))
        Write.Print(f''' [+] Finishing Decrypt the content \n''',
                    Colors.purple_to_red, interval=0.005)


doc = '''
      ______                              _                           _ 
     (____  \                            | |                         | |
      ____)  )_____  ____ ___ _____  ____| |  _ _____  ____ _____  __| |
     |  __  (| ___ |/ ___)___) ___ |/ ___) |_/ ) ___ |/ ___) ___ |/ _  |
     | |__)  ) ____| |  |___ | ____| |   |  _ (| ____| |   | ____( (_| |
     |______/|_____)_|  (___/|_____)_|   |_| \_)_____)_|   |_____)\____| 0.1
                
               [ Deobfuscator made by zqh#0684 aka .zqh on dc ]

                                
'''


b2 = r"""

  ,   A           {}
 / \, | ,        .--.
|    =|= >      /.--.\
 \ /` | `       |====|
  `   |         |`::`|
      |     .-;`\..../`;-.
     /\\/  /  |...::...|  \
     |:'\ |   /'''::'''\   |
      \ /\;-,/\   ::   /\--;
      |\ <` >  >._::_.<,<__>
      | `""`  /   ^^   \|  |
      |       |        |\::/
      |       |        |/|||
      |       |___/\___| '''
      |        \_ || _/
      |        <_ >< _>
      |        |  ||  |
      |        |  ||  |
      |       _\.:||:./_
      |      /____/\____\

"""
System.Size(160, 45)

Anime.Fade(Center.Center(b2), Colors.purple_to_red,
           Colorate.Vertical, enter=True)


def main():
    os.system('cls')
    _mix_colors = (Colors.orange, Colors.purple,
                   Colors.red, Colors.pink)
    print(Colorate.DiagonalBackwards(Colors.DynamicMIX(_mix_colors),
          Center.XCenter(Add.Add(doc, b2, center=True))))
    r = Berserkered()
    v = time.time()
    r.format()
    r.getkey()
    r.Unsparkled()
    r.decrypt_final_ouptut()
    c = time.time()
    Write.Input(
        f''' [!] Your File has been Successfully Unsparkled in {round(c-v)} seconds !''', Colors.purple_to_red, interval=0.005)
    main()


main()
```
## License

Distributed under the Apache License 2.0. See [LICENSE](https://github.com/99og/Thanatos_v1.0-Obfuscated-Challlenge/blob/main/LICENSE) for more information.

## Authors

* **The nicest guy on the planet** aka **zqh#0684 on discord** - *Python developer* - [.zqh](https://github.com/99og) - *Built ReadME Template*
