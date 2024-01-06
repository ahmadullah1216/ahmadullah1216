import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up the display
width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption('Simple Robot Simulation')

# Set up the robot
robot_color = (0, 255, 0)  # Green color
robot_width, robot_height = 50, 50
robot_x, robot_y = width // 2 - robot_width // 2, height // 2 - robot_height // 2
robot_speed = 5

# Main game loop
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    keys = pygame.key.get_pressed()

    # Move the robot based on key input
    if keys[pygame.K_LEFT]:
        robot_x -= robot_speed
    if keys[pygame.K_RIGHT]:
        robot_x += robot_speed
    if keys[pygame.K_UP]:
        robot_y -= robot_speed
    if keys[pygame.K_DOWN]:
        robot_y += robot_speed

    # Boundary checking
    robot_x = max(0, min(width - robot_width, robot_x))
    robot_y = max(0, min(height - robot_height, robot_y))

    # Draw the robot on the screen
    screen.fill((255, 255, 255))  # White background
    pygame.draw.rect(screen, robot_color, (robot_x, robot_y, robot_width, robot_height))

    # Update the display
    pygame.display.flip()

    # Control the frame rate
    pygame.time.Clock().tick(30)
