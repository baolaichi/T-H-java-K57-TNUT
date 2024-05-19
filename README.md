# T-H-java-K57-TNUT
Tính diện tích, chu vi của hình: tam giác, vuông, tròn, chữ nhật, lập phương:
Code:

package QLCB;

import javax.swing.*;
import java.awt.*;

public class ShapeCalculator extends JFrame {
    private CardLayout cardLayout;
    private JPanel mainPanel;

    public ShapeCalculator() {
        setTitle("Shape Calculator");
        setSize(400, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        cardLayout = new CardLayout();
        mainPanel = new JPanel(cardLayout);

        // Main menu panel
        JPanel menuPanel = new JPanel();
        menuPanel.setLayout(new GridLayout(5, 1));

        JButton triangleButton = new JButton("Tam giác");
        JButton squareButton = new JButton("Vuông");
        JButton circleButton = new JButton("Tròn");
        JButton rectangleButton = new JButton("Chữ nhật");
        JButton cubeButton = new JButton("Lập phương");

        menuPanel.add(triangleButton);
        menuPanel.add(squareButton);
        menuPanel.add(circleButton);
        menuPanel.add(rectangleButton);
        menuPanel.add(cubeButton);

        mainPanel.add(menuPanel, "Menu");

        // Add shape panels
        mainPanel.add(createTrianglePanel(), "Triangle");
        mainPanel.add(createSquarePanel(), "Square");
        mainPanel.add(createCirclePanel(), "Circle");
        mainPanel.add(createRectanglePanel(), "Rectangle");
        mainPanel.add(createCubePanel(), "Cube");

        add(mainPanel);

        triangleButton.addActionListener(e -> cardLayout.show(mainPanel, "Triangle"));
        squareButton.addActionListener(e -> cardLayout.show(mainPanel, "Square"));
        circleButton.addActionListener(e -> cardLayout.show(mainPanel, "Circle"));
        rectangleButton.addActionListener(e -> cardLayout.show(mainPanel, "Rectangle"));
        cubeButton.addActionListener(e -> cardLayout.show(mainPanel, "Cube"));

        setVisible(true);
    }

    private JPanel createTrianglePanel() {
        JPanel panel = new JPanel(new GridLayout(6, 2));

        JLabel baseLabel = new JLabel("Đáy:");
        JTextField baseField = new JTextField();
        JLabel heightLabel = new JLabel("Chiều cao:");
        JTextField heightField = new JTextField();
        JLabel sideLabel = new JLabel("Cạnh:");
        JTextField sideField = new JTextField();
        JButton calculateButton = new JButton("Tính toán");
        JLabel resultLabel = new JLabel("Kết quả:");
        JButton backButton = new JButton("Quay lại");

        panel.add(baseLabel);
        panel.add(baseField);
        panel.add(heightLabel);
        panel.add(heightField);
        panel.add(sideLabel);
        panel.add(sideField);
        panel.add(calculateButton);
        panel.add(resultLabel);
        panel.add(new JLabel()); // Empty cell for layout spacing
        panel.add(backButton);

        calculateButton.addActionListener(e -> {
            try {
                double base = Double.parseDouble(baseField.getText());
                double height = Double.parseDouble(heightField.getText());
                double side = Double.parseDouble(sideField.getText());
                double area = (base * height) / 2;
                double perimeter = 3 * side;
                resultLabel.setText(String.format("Diện tích: %.2f, Chu vi: %.2f", area, perimeter));
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Vui lòng nhập số hợp lệ");
            }
        });

        backButton.addActionListener(e -> cardLayout.show(mainPanel, "Menu"));

        return panel;
    }

    private JPanel createSquarePanel() {
        JPanel panel = new JPanel(new GridLayout(4, 2));

        JLabel sideLabel = new JLabel("Cạnh:");
        JTextField sideField = new JTextField();
        JButton calculateButton = new JButton("Tính toán");
        JLabel resultLabel = new JLabel("Kết quả:");
        JButton backButton = new JButton("Quay lại");

        panel.add(sideLabel);
        panel.add(sideField);
        panel.add(calculateButton);
        panel.add(resultLabel);
        panel.add(new JLabel()); // Empty cell for layout spacing
        panel.add(backButton);

        calculateButton.addActionListener(e -> {
            try {
                double side = Double.parseDouble(sideField.getText());
                double area = side * side;
                double perimeter = 4 * side;
                resultLabel.setText(String.format("Diện tích: %.2f, Chu vi: %.2f", area, perimeter));
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Vui lòng nhập số hợp lệ");
            }
        });

        backButton.addActionListener(e -> cardLayout.show(mainPanel, "Menu"));

        return panel;
    }

    private JPanel createCirclePanel() {
        JPanel panel = new JPanel(new GridLayout(4, 2));

        JLabel radiusLabel = new JLabel("Bán kính:");
        JTextField radiusField = new JTextField();
        JButton calculateButton = new JButton("Tính toán");
        JLabel resultLabel = new JLabel("Kết quả:");
        JButton backButton = new JButton("Quay lại");

        panel.add(radiusLabel);
        panel.add(radiusField);
        panel.add(calculateButton);
        panel.add(resultLabel);
        panel.add(new JLabel()); // Empty cell for layout spacing
        panel.add(backButton);

        calculateButton.addActionListener(e -> {
            try {
                double radius = Double.parseDouble(radiusField.getText());
                double area = Math.PI * radius * radius;
                double perimeter = 2 * Math.PI * radius;
                resultLabel.setText(String.format("Diện tích: %.2f, Chu vi: %.2f", area, perimeter));
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Vui lòng nhập số hợp lệ");
            }
        });

        backButton.addActionListener(e -> cardLayout.show(mainPanel, "Menu"));

        return panel;
    }

    private JPanel createRectanglePanel() {
        JPanel panel = new JPanel(new GridLayout(5, 2));

        JLabel lengthLabel = new JLabel("Chiều dài:");
        JTextField lengthField = new JTextField();
        JLabel widthLabel = new JLabel("Chiều rộng:");
        JTextField widthField = new JTextField();
        JButton calculateButton = new JButton("Tính toán");
        JLabel resultLabel = new JLabel("Kết quả:");
        JButton backButton = new JButton("Quay lại");

        panel.add(lengthLabel);
        panel.add(lengthField);
        panel.add(widthLabel);
        panel.add(widthField);
        panel.add(calculateButton);
        panel.add(resultLabel);
        panel.add(new JLabel()); // Empty cell for layout spacing
        panel.add(backButton);

        calculateButton.addActionListener(e -> {
            try {
                double length = Double.parseDouble(lengthField.getText());
                double width = Double.parseDouble(widthField.getText());
                double area = length * width;
                double perimeter = 2 * (length + width);
                resultLabel.setText(String.format("Diện tích: %.2f, Chu vi: %.2f", area, perimeter));
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Vui lòng nhập số hợp lệ");
            }
        });

        backButton.addActionListener(e -> cardLayout.show(mainPanel, "Menu"));

        return panel;
    }

    private JPanel createCubePanel() {
        JPanel panel = new JPanel(new GridLayout(4, 2));

        JLabel sideLabel = new JLabel("Cạnh:");
        JTextField sideField = new JTextField();
        JButton calculateButton = new JButton("Tính toán");
        JLabel resultLabel = new JLabel("Kết quả:");
        JButton backButton = new JButton("Quay lại");

        panel.add(sideLabel);
        panel.add(sideField);
        panel.add(calculateButton);
        panel.add(resultLabel);
        panel.add(new JLabel()); // Empty cell for layout spacing
        panel.add(backButton);

        calculateButton.addActionListener(e -> {
            try {
                double side = Double.parseDouble(sideField.getText());
                double area = 6 * side * side;
                double volume = side * side * side;
                resultLabel.setText(String.format("Diện tích bề mặt: %.2f, Thể tích: %.2f", area, volume));
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, "Vui lòng nhập số hợp lệ");
            }
        });

        backButton.addActionListener(e -> cardLayout.show(mainPanel, "Menu"));

        return panel;
    }

    public static void main(String[] args) {
        new ShapeCalculator();
    }
}

