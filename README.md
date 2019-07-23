# Ud5_Ejemplo2
_Ejemplo 2 de la Unidad 5._ 

Vamos a crear dos _Fragments_ de tal forma que tengan la mitad de la pantalla para cada uno. 
Por cada _Fragment_ que creemos debemos implementar su _layout_ y su clase asociada que deberá extender de la clase _Fragment_.

## _layouts_ de la aplicación
Creamos el _layout_ para cada _Fragment_.

_fragment_uno.xml_:
```<android.support.constraint.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@android:color/holo_blue_dark">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/fragment_uno"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</android.support.constraint.ConstraintLayout>
```

_fragment_dos.xml_:
```
<android.support.constraint.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@android:color/holo_green_dark">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/fragment_dos"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</android.support.constraint.ConstraintLayout>
```

Para que se aprecie bien lo que ocupa cada _Fragment_, usamos el atributo _background_ para pintar su fondo.

_activity_main.xml_:
```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <fragment
        android:id="@+id/fragment1"
        android:name="com.example.ud5_ejemplo2.FragmentUno"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="5"/>

    <fragment
        android:id="@+id/fragment2"
        android:name="com.example.ud5_ejemplo2.FragmentDos"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="5"/>

</LinearLayout>
```
Posicionamos los _Fragments_ utilizando un _LinearLayout_ dando el mismo peso a cada uno.

## Clases de la aplicación

Creamos una clase por cada _Fragment_.

_FragmentUno.java_:
```
public class FragmentUno extends Fragment {
    @Nullable
    @Override
    public View onCreateView(@NonNull LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        // "Inflamos" el Fragment
        View view = inflater.inflate(R.layout.fragment_uno, container, false);

        return view;
    }
}
```
_FragmentDos.java_:
```
public class FragmentDos extends Fragment {
    @Nullable
    @Override
    public View onCreateView(@NonNull LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        // "Inflamos" el Fragment
        View view = inflater.inflate(R.layout.fragment_dos, container, false);

        return view;
    }
}
```
Deben heredar de la clase _Fragment_ y sobrescribir el método _onCreateView_ donde se "inflará" el _Fragment_ usando su _layout_.

Por su parte, la clase principal no se modifica.

_MainActivity.java_:
```
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}
```
