# L6
Зубова Евгения 803в1
Добавляем поле EditText тип textMultiLine и 2 кнопки


....
  Activity_main.xml
  <EditText
        android:id="@+id/editTextTextMultiLine"
        android:layout_width="380dp"
        android:layout_height="42dp"
        android:ems="10"
        android:gravity="start|top"
        android:inputType="textMultiLine"
        tools:layout_editor_absoluteX="16dp"
        tools:layout_editor_absoluteY="16dp" />

    <Button
        android:id="@+id/button5"
        android:layout_width="215dp"
        android:layout_height="44dp"
        android:text="Получить данные"
        android:textSize="8sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button4"
        app:layout_constraintHorizontal_bias="0.015"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.122" />

    <Button
        android:id="@+id/button4"
        android:layout_width="193dp"
        android:layout_height="45dp"
        android:text="Сохранить данные"
        android:textSize="8sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toEndOf="@+id/button5"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.122" />

    <TextView
        android:id="@+id/saveTextView"
        android:layout_width="374dp"
        android:layout_height="31dp"
        android:text="TextView"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

Добавим код в MainActivity
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    protected void onSaveInstanceState(Bundle outState) {
        outState.putString(nameVariableKey, name);
        TextView nameView = (TextView) findViewById(R.id.saveTextView);

        outState.putString(textViewTexKey,
                nameView.getText().toString());
        super.onSaveInstanceState(outState);
    }

    @Override
    protected void onRestoreInstanceState(Bundle savedInstanceState) {
        super.onRestoreInstanceState(savedInstanceState);
        name = savedInstanceState.getString(nameVariableKey);
        String textViewText =
                savedInstanceState.getString(textViewTexKey);
        TextView nameView = (TextView) findViewById(R.id.saveTextView);
        nameView.setText(textViewText);
    }

    public void restoreField(View view) {
        TextView nameView = (TextView) findViewById(R.id.saveTextView);
        nameView.setText(name);
    }


    public void saveField(View view) {
        TextView nameBox = (TextView)
                findViewById(R.id.editTextTextMultiLine);
        name = nameBox.getText().toString();
    }
}


Результат
![image](https://user-images.githubusercontent.com/73265788/143987520-984a4be4-a1e8-46d8-abf9-6f360b5b9ebb.png)




