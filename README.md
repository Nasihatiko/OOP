# OOP
OOP lections
""" 
ООП - Объектно ориентированное программирование (парадигма)

Принципы ООП!

    "Основные"
        1. - Наследование
        1.2 - Множественное наследование
        2. - Полиморфизм
        3. - Инкапсуляция

    "Дополнительные"
        1. - Абстракция
        2. - Ассоциация
        2.1 - Астрегация
        2.2 - Композиция
"""

"""
Наследоание - принцип ООП, где мы можем в дочерном классе унаследовать, переопределять
и использовать все методы и аттрибуты родительского класса
"""

# class A:
#     def method1(self):
#         """Этот метод выводит строку"""
#         print("method1 in class A")
    
# class B(A):
#     """Наследовали все методы и атриуты класса А"""

# b = B() #Создали объект (экземпляр) от класса B
# b.method1() #Можем вызвать метод method1, который был создан в классе А

"""
--> Полиморфизм - принцип ООП, мы можем создавать в разных классах одноименные методы и аттрибуты с разным функционалом.
"""

# class A:
#     def __str__(self) -> str:
#         """Метод __str__ работает когда:
#         1. мы оборачиваем объект в str -> str(A())
#         2. принтим объект -> print(A())
#         """
#         return "A object"

# class B:
#     def __str__(self):
#         return "B object"

# print(A()) #"A object"
# print(B()) #"B object"
# print(A()) #"A object"
# print(A()) #"A object"
# print(B()) #"B object"

"""
--> Инкапсуляция - принцип ООП, где мы можем делать аттрибуты и методы с разным уровнем доступа
"""

# class A:
#     attribute1 = "публичный аттрибут"
#     _attribute2 = "защищенный аттрибут"
#     __attribute3 = "приватный аттрибут (но можно обратиться так: _A__attribute3)"

#     def method1(self):
#         return "публичный метод"
#     def _method2(self):
#         return "защищенный метод"
#     def __method3(self):
#         return "приватный метод (_A__method3)"

#A().__attribute3 -> AttributeError
#A()._A__attribute3 -> "приватный аттрибут (но можно обратиться так: _A__attribute3)"


"""Getters and Setters"""
# это методы, через которые мы можем получать (getter) и изменять (setter) значения защищенных и приватных аттрибутов.

class A:
    _attr1 = "защищенный аттрибут"
    __attr2 = "приватный аттрибут"

    def get_attr1(self):
        """Возвращает значения аттрибута _attr1"""
        return self._attr1

    def get_attr2(self):
        """Возвращает значения аттрибута __attr2"""
        return self.__attr2

    def set_attr1(self, value):
        """Меняет значения _attr1"""
        self._attr1 = value

    def set_attr2(self, value):
        """Меняет значения __attr2"""
        self.__attr2 = value

a = A()
print(a.get_attr1(), a.get_attr2())
a.set_attr1("New vall")
a.set_attr2("Val")
print(a.get_attr1(), a.get_attr2())


"""
Множественное наследование - принцип ООП, в котором мы наследуем все аттрибуты и методы у всех родителей
"""
# class A:
#     def method_a(self):
#         ...

# class B:
#     def method_b(self):
#         ...

# class C(A,B):
#     """Класс унаследовал все аттрибуты и методы класса А и класса B и все аттрибуты методы их родителей (object)"""
#     ...

# c = C()
# c.method_a()
# c.method_b()


"""Проблемы множественного наследования"""
# 1. - Проблема ромба (решена через mro)
# 2. - Проблема перекрестного наследования (не решена)
"""Проблема ромба"""
# class A:
#     """корневой класс"""
#     def method_a(self):
#         return "A"

#     # def __str__(self):
#     #     return "A"

# class B(A):
#     """Первый дочерний класс от А"""
#     def method_b(self):
#         return "B"

# class C(A):
#     """Второй дочерний класс от А"""
#     def method_c(self):
#         return "C"

# class D(B,C):
#     """дочерний класс от B,C"""
#     def method_d(self):
#         return "D"

# d = D()
# d.method_a()
# d.method_b()
# d.method_c()
# d.method_d()
# # print(D.mro())
# # print(D.__mro__)

# def mro(clas):
#     return list(clas.__mro__)
# print(mro(D))

# MRO - D -> B-> C -> A


"""Проблема перекрестного наследования"""

# class A:
#     ...

# class B:
#     ...

# class C(A,B):
#     ...

# class D(B,A):
#     ...

# class E(C,D): #--> TypeError: Cannot create a consistent method resolution order (MRO) for bases A, B
#     ...
