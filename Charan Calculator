import sys
from PyQt5.QtWidgets import (
    QApplication, QWidget, QLineEdit, QPushButton,
    QVBoxLayout, QGridLayout, QHBoxLayout
)
from PyQt5.QtCore import Qt


class Calculator(QWidget):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("Charan Calculator")
        self.setFixedSize(400,500)
        self.initUI()

    def initUI(self):
        self.layout = QVBoxLayout()
        self.input_line = QLineEdit()
        self.input_line.setAlignment(Qt.AlignRight)
        self.input_line.setReadOnly(True)
        self.input_line.setStyleSheet("font-size: 24px; padding: 10px;")

        self.layout.addWidget(self.input_line)
        self.create_buttons()
        self.setLayout(self.layout)

    def create_buttons(self):
        buttons = [
            ['7', '8', '9', '/'],
            ['4', '5', '6', '*'],
            ['1', '2', '3', '-'],
            ['0', '.', '=', '+']
        ]

        grid = QGridLayout()
        for row_idx, row in enumerate(buttons):
            for col_idx, button_text in enumerate(row):
                button = QPushButton(button_text)
                button.setFixedSize(60, 60)
                button.setStyleSheet("""
                    QPushButton {
                        font-size: 18px;
                        border: none;
                        background-color: #f0f0f0;
                    }
                    QPushButton:hover {
                        background-color: #d0d0d0;
                    }
                """)
                button.clicked.connect(self.on_button_click)
                grid.addWidget(button, row_idx, col_idx)

        clear_btn = QPushButton("C")
        clear_btn.setFixedSize(250, 40)
        clear_btn.setStyleSheet("""
            QPushButton {
                font-size: 16px;
                background-color: #ff4d4d;
                color: white;
                border: none;
            }
            QPushButton:hover {
                background-color: #e60000;
            }
        """)
        clear_btn.clicked.connect(self.clear_input)

        self.layout.addLayout(grid)
        self.layout.addWidget(clear_btn)

    def on_button_click(self):
        button = self.sender()
        text = button.text()

        if text == "=":
            try:
                result = str(eval(self.input_line.text()))
                self.input_line.setText(result)
            except:
                self.input_line.setText("Error")
        else:
            self.input_line.setText(self.input_line.text() + text)

    def clear_input(self):
        self.input_line.clear()


if __name__ == "__main__":
    app = QApplication(sys.argv)
    calc = Calculator()
    calc.show()
    sys.exit(app.exec_())
