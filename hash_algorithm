from math import ceil
import numpy as np
import matplotlib.pyplot as plt
from matplotlib import colors
from random import randint
import time

start_time = time.time()

plaintext = 'Съешь ещё этих французских булочек и выпей чаю.'
while len(plaintext) % 32 != 0:
    plaintext += '0'
M = []
s = 0

k = ceil(len(plaintext)/32)

for i in range(len(plaintext)):
    if i % k == 0:
        M.append(s)
        s = 0
    s += ord(plaintext[i])

def topple(grid):
    mask = grid > 3
    grid[:, 1:] += mask[:,:-1]
    grid[:, :-1] += mask[:,1:]
    grid[1:, :] += mask[:-1,:]
    grid[:-1, :] += mask[1:,:]
    grid -= mask*4

def draw_graph(grid):
    cmap = colors.ListedColormap(['black','yellow','orange','red'])
    bounds = [-.5, .5, 1.5, 2.5, 3.5]
    norm = colors.BoundaryNorm(bounds, cmap.N)
    heatmap = plt.pcolor(grid, cmap=cmap, norm=norm)

    plt.imshow(grid)
    plt.colorbar(heatmap, ticks=[0, 1, 2, 3])
    plt.show()

def run(grid_size):
    grid = np.zeros([grid_size, grid_size])
    for i in range(len(M)):
        for j in range(len(M)):
            if i == j:
                grid[i, j] = M[j]
    while grid.max() > 3:
        topple(grid)
    return grid

def main():
    grid_size = len(M)

    if grid_size % 2 == 0:
        grid_size += 1

    grid = run(grid_size)
    print("--- %s seconds ---" % (time.time() - start_time))
    draw_graph(grid)

if __name__ == "__main__":
    main()
