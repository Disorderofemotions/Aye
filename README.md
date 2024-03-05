    // Добавление минимум 10 сущностей
    for (int i = 0; i < 10; i++) {
        Book book = new Book.Builder()
                .setId((long) i)
                .setName("Book " + i)
                .setDescription("Description of Book " + i)
                .setIsdn("ISBN " + i)
                .setPrice(10.0 + i)
                .setDiscount(0.2)
                .setNumber(10 + i)
                .build();

        booksMap.put(book.id, book);
    }

    // Вывод информации о всех книгах
    for (Book book : booksMap.values()) {
        System.out.println(book);
    }

    Scanner scanner = new Scanner(System.in);
    int choice = 0;

    do {
        System.out.println("Выберите действие:");
        System.out.println("1. Посмотреть все книги");
        System.out.println("2. Добавить книгу");
        System.out.println("3. Удалить книгу");
        System.out.println("4. Выйти");

        choice = scanner.nextInt();

        switch (choice) {
            case 1:
                System.out.println("Информация о всех книгах:");
                for (Book book : booksMap.values()) {
                    System.out.println(book);
                }
                break;

            case 2:
                // Добавляем новую книгу
                Book newBook = new Book.Builder()
                        .setId((long) booksMap.size())
                        .setName("New Book")
                        .setDescription("Description of New Book")
                        .setIsdn("New ISBN")
                        .setPrice(15.0)
                        .setDiscount(0.1)
                        .setNumber(5)
                        .build();

                booksMap.put(newBook.id, newBook);
                System.out.println("Новая книга добавлена: " + newBook);
                break;

            case 3:
                // Удаляем книгу
                System.out.println("Введите ID книги для удаления:");
                Long idToRemove = scanner.nextLong();
                if (booksMap.containsKey(idToRemove)) {
                    booksMap.remove(idToRemove);
                    System.out.println("Книга успешно удалена");
                } else {
                    System.out.println("Книга с таким ID не найдена");
                }
                break;

            case 4:
                System.out.println("Выход из программы");
                break;

            default:
                System.out.println("Некорректный выбор, повторите попытку");
        }
    } while (choice != 4);
}
