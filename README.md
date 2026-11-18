# Часть 1
class Rival:
    life = 3
        def attack(self):
        print('uch!')
        self.life -=1
    def checkLife(self):
        if self.life <=0:
            print('You won!')
        else:
            print(self.life)

thanos = Rival()
thanos.checkLife()

thanos.attack()
thanos.attack()
thanos.attack()
thanos.checkLife()

magneto = Rival()
thanos.checkLife()
magneto.checkLife()

thanos.attack()
thanos.attack()
thanos.attack()
thanos.checkLife()
magneto.checkLife()

# Часть 2

import datetime

birthday = datetime.date(2017, 6, 1)
print(birthday)

x = datetime.datetime.now()
print(x.year)

print(x.year,x.month,x.day)

from datetime import date
birthday = date(2017, 6, 1)
print(birthday)

from datetime import date as d
birthday = d(2017, 6, 1)
print(birthday)

# Часть 3

class SoyuzDocking:
    def __init__(self):
        self.distance = 500
        self.speed = 50
        self.fuel = 100
    def perform_burn(self, burn_amount):
        self.speed = max(self.speed - burn_amount, 0)
        self.fuel = max(self.fuel - burn_amount, 0)
    def update_distance(self):
        self.distance = max(self.distance - self.speed, 0)
    def has_docked(self):
        return self.distance <= 0

docking_sequence = SoyuzDocking()

print('Добро пожаловать в симуляцию стыковки Союз Т-6!')
print('Ваша миссия – стыковка со станцией Салют-7.')
print('Вы можете управлять скоростью космического корабля сжигая топливо.')
print('Каждая единица сожженного топлива замедляет космический корабль на 1 м/с.')
print('Удачи экипажу!')

while not docking_sequence.has_docked():
    print(f'Расстояние до Салют-7: {docking_sequence.distance} метров')
    print(f'Скорость: {docking_sequence.speed} м/с')
    print(f'Топливо: {docking_sequence.fuel} кг')
    if docking_sequence.fuel <= 0:
        print('Кончилось топливо!')
        break
    if docking_sequence.distance < 11:
        autopilot = input(&#39;До станции Салют-7 осталось менее 11 метров. Активировать режим автопилота для автоматической стыковки? (да/нет)')
    if autopilot.lower() == 'да':
        print('Автопилот активирован.')
        break
    burn_amount = input('Сколько сжечь топлива для снижения скорости: ')
    burn_amount = int(burn_amount)
    docking_sequence.perform_burn(burn_amount)
    docking_sequence.update_distance()
    if docking_sequence.distance <= 11 and docking_sequence.speed <= docking_sequence.distance:
        print('Стыковка подтверждена. Поздравляем экипаж!')
    else:
        print('Миссия провалена. Союз Т-6 не смог состыковаться с Салют-7.')