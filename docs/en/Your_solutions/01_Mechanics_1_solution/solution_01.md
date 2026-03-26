import sympy as sp

def solve_kinematics():
    t = sp.symbols('t')

    # Определение вектора положения r(t)
    r_i = 3*t**2
    r_j = 5*t - 8*t**2

    # 1. Вычисление скорости v(t) = dr/dt
    v_i = sp.diff(r_i, t)
    v_j = sp.diff(r_j, t)

    # 2. Вычисление ускорения a(t) = dv/dt
    a_i = sp.diff(v_i, t)
    a_j = sp.diff(v_j, t)

    print("--- Результаты вычислений ---")
    print(f"Скорость v(t)     = ({v_i})i + ({v_j})j")
    print(f"Ускорение a(t)    = ({a_i})i + ({a_j})j")

if __name__ == "__main__":
    solve_kinematics()
