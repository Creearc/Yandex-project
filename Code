import pygame
import random

black = (0, 0, 0)
white = (255, 255, 255)
green = (0, 255, 0)
red = (255, 0, 0)
X = 800
Y = 800
x_speed = 0
y_speed = 0
x_coord = 10
y_coord = 10
border = 2
speed = 5
pos = [0, 0]
pos_2 = [1, 1]
s = 30
a = 0
q = 0
b = []
c = 0
pot = 1
TIMEREVENT = 30
pygame.init()
screen = pygame.display.set_mode([X, Y])
clock = pygame.time.Clock()
done = True
editor = False
w = []
asd = 0
f = None
circles = list()
poss = []
answer = []
check_1 = 999
check_2 = 999


class Finish:
    def __init__(self, pos_x, pos_y):
        self.pos_x = pos_x
        self.pos_y = pos_y

    def draw(self):
        pygame.draw.rect(screen, (0, 255, 0), [self.pos_x, self.pos_y, 50, 50])


class Ball:
    def __init__(self, x, y, step_x, step_y):
        self.x_monitor = 800
        self.y_monitor = 800
        self.pos = list(pos)
        self.pos_x = x
        self.pos_y = y
        self.step_x = step_x
        self.step_y = step_y

    def check(self):
        global w
        if self.pos_x <= 0:
            self.step_x *= -1
        if self.pos_x >= 800:
            self.step_x *= -1
        if self.pos_y <= 0:
            self.step_y *= -1
        if self.pos_y >= 800:
            self.step_y *= -1
        for i in w:
            i.collision_x(self.pos_x, self.pos_y, 0, self.step_x)
            i.collision_y(self.pos_x, self.pos_y, 0, self.step_y)

    def collision_x(self, x, y, x_speed):
        bx = True
        if x + x_speed > self.pos_x and x + x_speed < self.pos_x:
            if y > self.pos_y and y < self.pos_y:
                bx = False
        return bx

    def collision_y(self, x, y, y_speed):
        by = True
        if y + s + y_speed > self.pos_y and y + y_speed < self.pos_y:
            if x + s > self.pos_x and x < self.pos_x:
                by = False
        return by

    def draw(self):
        self.pos_x += self.step_x
        self.pos_y += self.step_y
        self.check()
        pygame.draw.circle(screen, (0, 0, 0), (self.pos_x, self.pos_y), 10)


class Wall:
    def __init__(self, pos_x, pos_y, pos_x2, pos_y2):
        self.pos_x = pos_x
        self.pos_y = pos_y
        self.pos_x2 = pos_x2
        self.pos_y2 = pos_y2

    def draw(self):
        pygame.draw.rect(screen, (0, 0, 255),
                         [self.pos_x, self.pos_y, self.pos_x2 - self.pos_x,
                          self.pos_y2 - self.pos_y])

    def collision_x(self, x, y, s, x_speed):
        bx = True
        if x + s + x_speed > self.pos_x and x + x_speed < self.pos_x2:
            if y + s > self.pos_y and y < self.pos_y2:
                bx = False
        return bx

    def collision_y(self, x, y, s, y_speed):
        by = True
        if y + s + y_speed > self.pos_y and y + y_speed < self.pos_y2:
            if x + s > self.pos_x and x < self.pos_x2:
                by = False
        return by


def draw_background(screen):
    screen.fill(white)


def draw_item(screen, color, x, y):
    pygame.draw.rect(screen, color, [0 + x, 0 + y, s, s])
    pygame.draw.rect(screen, (0, 0, 0), (0 + x, 0 + y, s, s), border)
    if pot == 0:
        f.draw()
    for i in w:
        i.draw()
    for i in b:
        i.draw()


def motion_x(x_coord, y_coord, x_speed, s, border):
    global asd
    bx = True
    for i in b:
        bx = i.collision_x(x_coord, y_coord, x_speed)
        if bx == False:
            x_coord = 0
            y_coord = 0
            asf(asd)
    for i in w:
        bx = i.collision_x(x_coord, y_coord, s + border, x_speed)
        if bx == False:
            break
    if x_speed != 0:
        if bx:
            if x_coord + x_speed >= X - 30:
                x_coord = X - 30
            elif x_coord + x_speed <= 0:
                x_coord = 0
            else:
                x_coord += x_speed
    return x_coord


def motion_y(x_coord, y_coord, y_speed, s, border):
    global asd
    by = True
    for i in b:
        by = i.collision_y(x_coord, y_coord, y_speed)
        if by == False:
            x_coord = 0
            y_coord = 0
            asf(asd)
    for i in w:
        by = i.collision_y(x_coord, y_coord, s + border, y_speed)
        if by == False:
            break
    if y_speed != 0:
        if by:
            if y_coord + y_speed >= Y - 30:
                y_coord = Y - 30
            elif y_coord + y_speed <= 0:
                y_coord = 0
            else:
                y_coord += y_speed
    return y_coord


def begining():
    global x_coord, y_coord,w , b
    w = []
    b = []
    x_coord, y_coord = 0, 0
    screen.fill(white)


def level_1():
    global f, w, check_1, check_2, asd
    begining()
    asd = 1
    f = Finish(750, 750)
    for i in range(100, 800, 100):
        for j in range(100, 800, 100):
            w.append(Wall(i, j, i + 50, j + 50))
    check_1 = 750
    check_2 = 750


def level_2():
    global f, w, check_1, check_2, asd
    begining()
    asd = 2
    f = Finish(750, 750)
    check_1 = 750
    check_2 = 750
    for i in range(100, 800, 100):
        for j in range(100, 800, 100):
            q = random.randrange(0, 2, 1)
            if q == 1:
                w.append(Wall(i, j, i + 50, j + 50))


def level_3():
    global f, w, check_1, check_2, asd, b
    begining()
    draw_background(screen)
    asd = 3
    f = Finish(400, 400)
    check_1 = 400
    check_2 = 400
    b.append(Ball(100, 150, 5, 5))
    w.append(Wall(200, 250, 600, 350))
    w.append(Wall(200, 250, 300, 500))
    w.append(Wall(200, 500, 500, 550))


def level_4():
    global f, w, check_1, check_2, asd, b
    begining()
    asd = 4
    b.append(Ball(100, 150, 5, 5))
    f = Finish(750, 750)
    check_1 = 750
    check_2 = 750
    begining()


def level_5():
    global f, w, check_1, check_2, asd
    begining()
    asd = 5
    f = Finish(400, 750)
    check_1 = 400
    check_2 = 750
    draw_background(screen)
    b.append(Ball(100, 200, 0, 5))
    b.append(Ball(200, 200, 0, 5))
    b.append(Ball(300, 200, 0, 5))
    b.append(Ball(400, 200, 0, 5))
    b.append(Ball(500, 200, 0, 5))
    b.append(Ball(600, 200, 0, 5))
    w.append(Wall(0, 500, 700, 600))
    w.append(Wall(50, 200, 800, 300))


def asf(asd):
    global w, b, check_1, check_2
    w = []
    b = []
    check_1 = 999
    check_2 = 999
    if asd == 1:
        level_1()
    if asd == 2:
        level_2()
    if asd == 3:
        level_3()
    if asd == 4:
        level_4()
    if asd == 5:
        level_5()
    if asd == 0:
        menu()


def menu():
    global asd
    draw_background(screen)
    pygame.draw.rect(screen, (0, 0, 0), (350, 150, 100, 50), 2)
    pygame.draw.rect(screen, (0, 0, 0), (350, 250, 100, 50), 2)
    pygame.draw.rect(screen, (0, 0, 0), (350, 350, 100, 50), 2)
    pygame.draw.rect(screen, (0, 0, 0), (350, 450, 100, 50), 2)
    pygame.draw.rect(screen, (0, 0, 0), (350, 550, 100, 50), 2)
    pygame.draw.rect(screen, (0, 0, 0), (350, 650, 100, 50), 2)
    pygame.draw.line(screen, (0, 0, 0), [400, 160], [400, 190], 4)  # 1
    pygame.draw.line(screen, (0, 0, 0), [390, 260], [390, 290], 4)  # 2
    pygame.draw.line(screen, (0, 0, 0), [410, 260], [410, 290], 4)  # 2
    pygame.draw.line(screen, (0, 0, 0), [400, 360], [400, 390], 4)  # 3
    pygame.draw.line(screen, (0, 0, 0), [380, 360], [380, 390], 4)  # 3
    pygame.draw.line(screen, (0, 0, 0), [420, 360], [420, 390], 4)  # 3
    pygame.draw.line(screen, (0, 0, 0), [390, 460], [390, 490], 4)  # 4
    pygame.draw.line(screen, (0, 0, 0), [400, 460], [410, 490], 4)  # 4
    pygame.draw.line(screen, (0, 0, 0), [420, 460], [410, 490], 4)  # 4
    pygame.draw.line(screen, (0, 0, 0), [390, 560], [400, 590], 4)  # 5
    pygame.draw.line(screen, (0, 0, 0), [410, 560], [400, 590], 4)  # 5
    pygame.draw.line(screen, (0, 0, 0), [395, 660], [405, 690], 4)  # exit
    pygame.draw.line(screen, (0, 0, 0), [405, 660], [395, 690], 4)  # exit


while done:
    draw_background(screen)
    if pot == 1:
        menu()
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            done = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_v:
                editor = not editor
                screen.fill(white)
                print(editor)
            if event.key == pygame.K_a:
                x_speed = -speed
            if event.key == pygame.K_d:
                x_speed = speed
            if event.key == pygame.K_w:
                y_speed = -speed
            if event.key == pygame.K_s:
                y_speed = speed
            if pot == 1:
                if event.key == pygame.K_SPACE:
                    if x_coord >= 350 and x_coord <= 450:
                        if y_coord >= 150 and y_coord <= 200:
                            level_1()
                            pot = 0
                        if y_coord >= 250 and y_coord <= 300:
                            level_2()
                            pot = 0
                        if y_coord >= 350 and y_coord <= 400:
                            level_3()
                            pot = 0
                        if y_coord >= 450 and y_coord <= 500:
                            level_4()
                            pot = 0
                        if y_coord >= 550 and y_coord <= 600:
                            level_5()
                            pot = 0
                        if y_coord >= 650 and y_coord <= 700:
                            pygame.quit()
            if event.key == pygame.K_ESCAPE:
                begining()
                pot = 1
                w = []
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_a:
                x_speed = 0
            if event.key == pygame.K_d:
                x_speed = 0
            if event.key == pygame.K_w:
                y_speed = 0
            if event.key == pygame.K_s:
                y_speed = 0
        if editor:
            if event.type == pygame.MOUSEBUTTONDOWN:
                pos = event.pos
            if event.type == pygame.MOUSEBUTTONUP:
                pos_2 = event.pos
                w.append(Wall(pos[0], pos[1], pos_2[0], pos_2[1]))
                print('w.append(Wall(%d, %d, %d, %d))' % (pos[0], pos[1], pos_2[0], pos_2[1]))
    x_coord = motion_x(x_coord, y_coord, x_speed, s, border)
    y_coord = motion_y(x_coord, y_coord, y_speed, s, border)
    draw_item(screen, red, x_coord, y_coord)
    if x_coord >= check_1 and x_coord - 50 <= check_1:
        if y_coord >= check_2 and y_coord - 50 <= check_2:
            print('WIN')
            pot = 1
            b = []
            w = []
            f = None
            check_1 = 999
            check_2 = 999
    pygame.display.flip()
    clock.tick(60)
pygame.quit()
