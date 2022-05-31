## Código para un formulario de registro en base de datos



### Código html


```markdown
<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <link href="EstilosTarj.css" rel="stylesheet" />
    <link href="Estilos.css" rel="stylesheet" />
        <title>Registro</title>
   
    <style type="text/css">
        .auto-style1 {
            width: 100%;
        }
    </style>
   
</head>
<body>
<div>
    <fieldset>
               <h1>Por favor ingrese los datos solicitados</h1>

        <form  class="form">

                        <table class="auto-style1">
                            <tr>
                                <td>
                        <Label ID="lblID" ></Label>
                                </td>
                                <td>
                        <TextBox  ID="txtID" ></TextBox>
     
                                </td>
                            </tr>
                            <tr>
                                <td>
                                    </td>
                                <td>
                                    </td>
                            </tr>
                            <tr>
                                <td>
                        <Label ID="lblNombre" runat="server" Text="Apellidos"></Label>
                                </td>
                                <td>
                        <TextBox ID="txtNombre" ><TextBox>
                                </td>
                            </tr>
                            <tr>
                                <td>
                                    </td>
                                <td>
                                    </td>
                            </tr>
                            <tr>
                                <td>
                        <Label ID="lblContra"  Text="Correo"></Label>
                                </td>
                                <td>
                        <TextBox  ID="txtContra"   ></TextBox>
                                </td>
                            </tr>
                            <tr>
                                <td>
                                    </td>
                                <td>
                                    </td>
                            </tr>
                            <tr>
                                <td>
                                    </td>
                                <td>
                                    </td>
                            </tr>
                        </table>
            <Button ID="Btnregistro" Text="Registrar" CssClass="btnregistro" OnClick="Btnregistro_Click"  />
            <Label ID="lblerror" ></Label>
   
            </form>
        </fieldset>
    </div>
    


</body>
</html>
```

### Código para conectarse a la base de datos 
```markdown
            string Nom = txtID.Text;
            string Ape = txtNombre.Text;
            string Correo = txtContra.Text;
            string exito = "Se agregaron los datos correctamente";
            string error = "Hubo un error agregando al usuario";
           try
            {



                 SqlConnection conexion = new SqlConnection("Data Source=suservidorBD;Initial Catalog=Base de datos a ocupar;Integrated Security= True");
                 conexion.Open();
                 string cadena = "insert into Usuarios (Nombre,Apellidos,Correo)  values ('" + Nom + "', '" + Ape + "','" +Correo+ "')";
                 SqlCommand comando = new SqlCommand(cadena, conexion);
                 comando.ExecuteNonQuery();
                 conexion.Close();
                 lblerror.Text = exito;

            }
            catch(Exception ex)
            {
                lblerror.Text = error;

            }
```

