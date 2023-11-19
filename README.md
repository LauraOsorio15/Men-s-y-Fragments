# Men-s-y-Fragments
<!-- main_menu.xml -->
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/menu_contacto"
        android:title="Contacto"/>
    <item
        android:id="@+id/menu_acerca_de"
        android:title="Acerca De"/>
</menu>
import android.content.Intent;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.main_menu, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()) {
            case R.id.menu_contacto:
                // Abrir la pantalla de contacto
                abrirPantallaContacto();
                return true;
            case R.id.menu_acerca_de:
                // Abrir la pantalla Acerca De
                abrirPantallaAcercaDe();
                return true;
            default:
                return super.onOptionsItemSelected(item);
        }
    }

    private void abrirPantallaContacto() {
        Intent intent = new Intent(this, ContactoActivity.class);
        startActivity(intent);
    }

    private void abrirPantallaAcercaDe() {
        Intent intent = new Intent(this, AcercaDeActivity.class);
        startActivity(intent);
    }
}
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class ContactoActivity extends AppCompatActivity {

    private EditText editTextNombre, editTextCorreo, editTextMensaje;
    private Button btnEnviarComentario;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_contacto);

        editTextNombre = findViewById(R.id.editTextNombre);
        editTextCorreo = findViewById(R.id.editTextCorreo);
        editTextMensaje = findViewById(R.id.editTextMensaje);
        btnEnviarComentario = findViewById(R.id.btnEnviarComentario);

        btnEnviarComentario.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                enviarComentario();
            }
        });
    }

    private void enviarComentario() {
        String nombre = editTextNombre.getText().toString();
        String correo = editTextCorreo.getText().toString();
        String mensaje = editTextMensaje.getText().toString();

        // Aquí puedes implementar la lógica para enviar el correo utilizando JavaMail

        // Muestra un mensaje de éxito (simulado)
        String mensajeExito = "Comentario enviado:\nNombre: " + nombre +
                "\nCorreo: " + correo +
                "\nMensaje: " + mensaje;

        Toast.makeText(this, mensajeExito, Toast.LENGTH_LONG).show();
    }
}
import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class AcercaDeActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_acerca_de);
        // Puedes agregar aquí la información de la bio del desarrollador
    }
}
import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class AcercaDeActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_acerca_de);
        // Puedes agregar aquí la información de la bio del desarrollador
    }
}
<!-- activity_contacto.xml -->
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <!-- EditText de Material Design -->
    <com.google.android.material.textfield.TextInputLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp">

        <com.google.android.material.textfield.TextInputEditText
            android:id="@+id/editTextNombre"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Nombre"/>
    </com.google.android.material.textfield.TextInputLayout>

    <com.google.android.material.textfield.TextInputLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/editTextNombre"
        android:layout_marginBottom="16dp">

        <com.google.android.material.textfield.TextInputEditText
            android:id="@+id/editTextCorreo"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:inputType="textEmailAddress"
            android:hint="Correo electrónico"/>
    </com.google.android.material.textfield.TextInputLayout>

    <com.google.android.material.textfield.TextInputLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/editTextCorreo"
        android:layout_marginBottom="16dp">

        <com.google.android.material.textfield.TextInputEditText
            android:id="@+id/editTextMensaje"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:inputType="textMultiLine"
            android:hint="Mensaje"/>
    </com.google.android.material.textfield.TextInputLayout>

    <Button
        android:id="@+id/btnEnviarComentario"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enviar Comentario"
        android:layout_below="@id/editTextMensaje"/>
</RelativeLayout>
<!-- activity_acerca_de.xml -->
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <!-- Puedes agregar información sobre el desarrollador aquí -->
</RelativeLayout>
