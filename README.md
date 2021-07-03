## CppGram İstifadəsi

~~~c++ c
#include "cppgram/cppgram.hpp"

using namespace cppgram;

//  Bot sinifin qururuq
class MyBot : public BasicBot<MyBot> {
public:
  MyBot(string &token) : BasicBot(token, "CppAzBot", this) {}

  MyBot(const MyBot &b) : BasicBot(b, this) {}
};

//  Bütün mesajları cavablandırır
void helloWorld(MyBot &bot,
                    const types::Message &message) {

// "Salam, Xoş Gəlmisiz" mesajı göndərir
bot.sendMessage("Salam, Xoş Gəlmisi");
}

int main() {
  std::string token = "token";
  auto bot = MyBot(token);
  // Hello World funksiyamızdan istifadə edirik cavablamaq üçün
  bot.processMessage = &helloWorld;
  auto poll = Polling<MyBot>(bot, 8);
  / aktif edirik
  poll.run();
}
~~~
## Müəllif

Cppgram kitabxanası [Danilo Spinella](github.com/DanySpin97) tərəfindən hazırlaıb
