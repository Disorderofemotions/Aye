допиши в код чтобы при вводе букв в строки х и у писало об ошибке:
import java.util.Scanner;

public class MatrixDeterminant {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Введите количество строк матрицы: ");
        int x = scanner.nextInt();
        System.out.print("Введите количество столбцов матрицы: ");
        int y = scanner.nextInt();

        int[][] matrix = new int[x][y];
        System.out.println("Введите элементы матрицы:");

        for (int i = 0; i < x; i++) {
            for (int j = 0; j < y; j++) {
                while (!scanner.hasNextInt()) {
                    System.out.println("Ошибка: введите число");
                    scanner.next();
                }
                matrix[i][j] = scanner.nextInt();
            }
        }

        System.out.println("Определитель матрицы: " + determinant(matrix));
    }

    public static int determinant(int[][] matrix) {
        int n = matrix.length;

        if (n == 1) {
            return matrix[0][0];
        }

        int det = 0;
        int sign = 1;

        for (int i = 0; i < n; i++) {
            int[][] subMatrix = new int[n - 1][n - 1];

            for (int j = 1; j < n; j++) {
                for (int k = 0; k < n; k++) {
                    if (k < i) {
                        subMatrix[j - 1][k] = matrix[j][k];
                    } else if (k > i) {
                        subMatrix[j - 1][k - 1] = matrix[j][k];
                    }
                }
            }

            det += sign * matrix[0][i] * determinant(subMatrix);
            sign = -sign;
        }

        return det;
    }
}
