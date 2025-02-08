# Quick_Sort
O Quick Sort é um algoritmo de ordenação que usa a estratégia Dividir para Conquistar. Ele escolhe um pivô, particiona a lista em elementos menores e maiores que o pivô e ordena recursivamente. Tem complexidade média O(n log n), sendo rápido na prática, mas pode atingir O(n²) no pior caso se a escolha do pivô for ruim.

import java.util.Arrays;

public class QuickSort {

    public static void quickSort(int[] arr, int left, int right) {
        if (left < right) {
             int pivotIndex = partition(arr, left, right);
            System.out.println("Após a partição com pivô " + arr[pivotIndex] + ":");
            printArray(arr);
            System.out.println();
            quickSort(arr, left, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, right);
        }
    }
    private static int partition(int[] arr, int left, int right) {
        int pivot = arr[right];
        int i = left - 1;
        for (int j = left; j < right; j++) {
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        int temp = arr[i + 1];
        arr[i + 1] = arr[right];
        arr[right] = temp;

        return i + 1;
    }
    public static void main(String[] args) {
        int[] arr = {38, 27, 43, 3, 9, 82, 10,56,48,59};
        System.out.println("Array antes da ordenação:");
        printArray(arr);
        System.out.println();
        quickSort(arr, 0, arr.length - 1);
        System.out.println("\nArray após a ordenação:");
        printArray(arr);
    }
    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
