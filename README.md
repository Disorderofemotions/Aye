     Scanner sc = new Scanner(System.in);
        try {
            int i = sc.nextInt();
            System.out.printf("норм " + i);
        } catch (InputMismatchException e) {
            sc.next(); // магия тут
            System.out.println("ввели не число");
        }
