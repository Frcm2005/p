# p
 frcm
import pygame
import sys

# Inicialização do Pygame
pygame.init()

# Configurações do jogo
screen_width = 800
screen_height = 600
pacman_speed = 5

# Cores
black = (0, 0, 0)
yellow = (255, 255, 0)

# Configurações do Pac-Man
pacman_radius = 30
pacman_x = screen_width // 2
pacman_y = screen_height // 2
mouth_angle = 0

# Inicialização da tela
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Pac-Man")

# Loop principal do jogo
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Controles do Pac-Man
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        pacman_x -= pacman_speed
    if keys[pygame.K_RIGHT]:
        pacman_x += pacman_speed
    if keys[pygame.K_UP]:
        pacman_y -= pacman_speed
    if keys[pygame.K_DOWN]:
        pacman_y += pacman_speed

    # Limpar a tela
    screen.fill(black)

    # Desenhar o Pac-Man
    pygame.draw.circle(screen, yellow, (pacman_x, pacman_y), pacman_radius)
    mouth_rect = pygame.Rect(pacman_x - pacman_radius, pacman_y - pacman_radius, pacman_radius * 2, pacman_radius * 2)
    pygame.draw.pie(screen, black, mouth_rect, 30 + mouth_angle, 330 - mouth_angle)

    # Atualizar a tela
    pygame.display.update()

    # Atualizar o ângulo da boca
    mouth_angle = (mouth_angle + 5) % 30

    # Limitar a taxa de quadros
    pygame.time.delay(50)

# Encerrar o jogo
pygame.quit()
sys.exit()
