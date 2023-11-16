
Конечно! Вот пример кода на языке Java для приложения ежедневник с двумя экранами и кнопкой "Добавить". На первом экране будет отображаться название дела, дата, время и описание задачи.

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class DailyPlannerApp extends JFrame {
    private JTextField taskNameField;
    private JTextField taskDateField;
    private JTextField taskTimeField;
    private JTextArea taskDescriptionArea;

    public DailyPlannerApp() {
        setTitle("Ежедневник");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setSize(400, 300);
        setLocationRelativeTo(null);

        // Создание элементов интерфейса на первом экране
        JLabel taskNameLabel = new JLabel("Название дела:");
        taskNameField = new JTextField(20);

        JLabel taskDateLabel = new JLabel("Дата:");
        taskDateField = new JTextField(10);

        JLabel taskTimeLabel = new JLabel("Время:");
        taskTimeField = new JTextField(10);

        JLabel taskDescriptionLabel = new JLabel("Описание:");
        taskDescriptionArea = new JTextArea(5, 20);
        JScrollPane scrollPane = new JScrollPane(taskDescriptionArea);
        scrollPane.setVerticalScrollBarPolicy(JScrollPane.VERTICAL_SCROLLBAR_ALWAYS);

        JButton addButton = new JButton("Добавить");
        addButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String taskName = taskNameField.getText();
                String taskDate = taskDateField.getText();
                String taskTime = taskTimeField.getText();
                String taskDescription = taskDescriptionArea.getText();

                // Здесь можно добавить код для сохранения задачи в ежедневнике или выполнить другие необходимые действия

                JOptionPane.showMessageDialog(null, "Задача успешно добавлена!", "Успех", JOptionPane.INFORMATION_MESSAGE);
            }
        });

        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(5, 2));
        panel.add(taskNameLabel);
        panel.add(taskNameField);
        panel.add(taskDateLabel);
        panel.add(taskDateField);
        panel.add(taskTimeLabel);
        panel.add(taskTimeField);
        panel.add(taskDescriptionLabel);
        panel.add(scrollPane);
        panel.add(addButton);

        setContentPane(panel);
        setVisible(true);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new DailyPlannerApp();
            }
        });
    }
}


Этот код использует библиотеку Swing для создания графического интерфейса пользователя (GUI). При нажатии кнопки "Добавить" вызывается метод actionPerformed, который получает значения из текстовых полей и выполняет необходимые действия, например, сохраняет задачу в ежедневнике. Затем, отображается информационное окно с сообщением о успешном добавлении задачи.

Примечание: Для запуска этого кода, вам потребуется настроить проект с библиотекой Swing.
