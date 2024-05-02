class N:
    def __init__(self, d):
        self.d = d
        self.n = None

class L:
    def __init__(self):
        self.h = None

    def a(self, d):
        n = N(d)
        if not self.h:
            self.h = n
            return
        l = self.h
        while l.n:
            l = l.n
        l.n = n

    def f(self, k):
        l = self.h
        while l:
            if l.d == k:
                return True
            l = l.n
        return False

    def r(self, k):
        l = self.h
        if l and l.d == k:
            self.h = l.n
            return
        p = None
        while l and l.d != k:
            p, l = l, l.n
        if not l:
            return
        p.n = l.n

def t(n):
    s = str(n)
    ll = L()
    for d in s:
        ll.a(int(d))
    return ll


n = 12345
ll = t(n)
print("Список из числа", n, ":", end=" ")
c = ll.h
while c:
    print(c.d, end=" ")
    c = c.n
print()


k = 3
if ll.f(k):
    print("Такого", k, "найден в списке")
else:
    print("Такого", k, "не найдено в списке")


k_to_remove = 4
ll.r(k_to_remove)
print("Когда произошло удаление", k_to_remove, "список стал:", end=" ")
c = ll.h
while c:
    print(c.d, end=" ")
    c = c.n
print()

