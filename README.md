🚗 مشروع التحكم في 4 محركات DC باستخدام Arduino و L293D
🔹 فكرة المشروع

يهدف هذا المشروع إلى التحكم في أربع محركات DC باستخدام Arduino Uno و L293D Motor Driver لتنفيذ الحركات التالية:
1️⃣ الحركة للأمام لمدة 30 ثانية.
2️⃣ الحركة للخلف لمدة دقيقة.
3️⃣ التبديل بين اليمين واليسار بالتناوب لمدة دقيقة.


// تعريف المنافذ
const int IN1 = 7;  // المحرك الأمامي الأيسر
const int IN2 = 8;
const int IN3 = 9;  // المحرك الأمامي الأيمن
const int IN4 = 10;
const int IN5 = 11; // المحرك الخلفي الأيسر
const int IN6 = 12;
const int IN7 = 13; // المحرك الخلفي الأيمن
const int IN8 = 14;

void setup() {
  // ضبط جميع المنافذ كمخارج
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  pinMode(IN5, OUTPUT);
  pinMode(IN6, OUTPUT);
  pinMode(IN7, OUTPUT);
  pinMode(IN8, OUTPUT);
}

void loop() {
  // 1️⃣ الحركة للأمام لمدة 30 ثانية
  forward();
  delay(30000);

  // 2️⃣ الحركة للخلف لمدة 60 ثانية
  backward();
  delay(60000);

  // 3️⃣ التبديل بين اليمين واليسار لمدة 60 ثانية
  for (int i = 0; i < 30; i++) { // 30 مرة * 2 ثواني = 60 ثانية
    turnRight();
    delay(1000);
    turnLeft();
    delay(1000);
  }

  // إيقاف المحركات بعد الانتهاء
  stopMotors();
}

// 🔹 الحركة للأمام
void forward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  digitalWrite(IN5, HIGH);
  digitalWrite(IN6, LOW);
  digitalWrite(IN7, HIGH);
  digitalWrite(IN8, LOW);
}

// 🔹 الحركة للخلف
void backward() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  digitalWrite(IN5, LOW);
  digitalWrite(IN6, HIGH);
  digitalWrite(IN7, LOW);
  digitalWrite(IN8, HIGH);
}

// 🔹 الدوران لليمين
void turnRight() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  digitalWrite(IN5, LOW);
  digitalWrite(IN6, HIGH);
  digitalWrite(IN7, HIGH);
  digitalWrite(IN8, LOW);
}

// 🔹 الدوران لليسار
void turnLeft() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  digitalWrite(IN5, HIGH);
  digitalWrite(IN6, LOW);
  digitalWrite(IN7, LOW);
  digitalWrite(IN8, HIGH);
}

// 🔹 إيقاف المحركات
void stopMotors() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
  digitalWrite(IN5, LOW);
  digitalWrite(IN6, LOW);
  digitalWrite(IN7, LOW);
  digitalWrite(IN8, LOW);
}

ضع  الكود tinkercad
