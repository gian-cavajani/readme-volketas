### 1. Asignar una IP Elástica

Primero, se necesita asignar una IP elástica a tu cuenta de AWS.

1.  Iniciar sesión en la Consola de administración de AWS y abrir el servicio EC2.
2.  En el panel de navegación de la izquierda, seleccionar "Direcciones IP elásticas".  
    ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeYQv1TDkbYmSf8OyJNc4z7mD83_chYieOpNi4tCWJJB7U3c2Sy4gOAv08GxRQUYfQ4NwtXn4RDp5_cEHHXfdbw4XAPRSZZMRzCoPtMDJJegBgHQaOSnJdoJi5JWoo00wWoHvTUF69nYy435-R3P9duQmgu?key=EcI-pi8eK7KHXtGxrQrIfA)
3.  Hacer clic en "Asignar nueva dirección IP elástica".  
    ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdVxL7QLyDSSZK2wzP2OWFYAYiY2-p0koEzyZMLztwoWJfIzsXCeYnMeLdTEDfcxnaHjf0RVd0ozolVqva2CzoEBHcb_jHR9q3jcDe42RUKrM6ACX-ZCSLqXHAjBkXZEk4cI8t_YCaUKqA_gck30YX009s?key=EcI-pi8eK7KHXtGxrQrIfA)
4.  Seleccionar "Asignar" para obtener una nueva IP elástica.
    1.  En la sección de "Configuraciones de la dirección IP elástica": Dejar todas las opciones en default.
    2.  En "Etiquetas": opcionalmente poner un nombre descriptivo para referenciar la IP y luego poder asociarla mas fácilmente.
        ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXevF-sCqn7M081H19dCJo2hvo64SqwE7eEmDZFcu5Uy77SDy9MD7ObXUEpV1IIDKLmLSp8WItVoYEQi5Ty6V1StIDPJkcNrDAms44p1LaKkVmkg6bFcwVdOjAmSoHplt_npttP4fcCwRhrlHcOPlusfRl1D?key=EcI-pi8eK7KHXtGxrQrIfA)

### 2. Asociar la IP Elástica a la Instancia EC2

Una vez que creadas la IP elásticas, debemos asociarla a las instancias EC2.

1.  En el Panel de Direcciones IP elásticas, hacer clic en "Asociar dirección IP elástica".  
    ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcQtzHnFfYslu_AtoEnR4i1kpFJihl_s0oN6AdQLLAb_10hj1vY_vtIZ8rKIA7c-0j8XLXLJaPcZ_wxC2i6mIf8q1Z_axu_WisqsCZcprx6nqPXu97ncWCmwtYRPiNgCdHK3rEOttZMZmR9W9lFbB7_esQO?key=EcI-pi8eK7KHXtGxrQrIfA)

2.  En el campo "Instancia", selecciona la instancia EC2 a la que deseas asociar la IP.  
    ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXebduAWJStBVogKQRK9-ETYVFWkN7v3IjNmrj5SthR89OixToA7G9yR90yfXve4XzJcgywnpxlvY_nYWhrexj1bUzbaMGp2rVHRjG2W3u4vtluPH8wx3d7B1b14d71iCUFXExs_FnNJHxpBuTxIxo7hp4rn?key=EcI-pi8eK7KHXtGxrQrIfA)

3.  Hacer clic en "Asociar".

### Verificación:

1.  En la pestaña de Instancias se puede observar las IP elásticas configuradas:
    ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc0u8jEysrmbLqnCF2ubBrnT1V-iKG6loM1_jUPFklztMaEFNAFazkgz-VZoI5t09IWpHv3e0Jf4jxNOnnlUKW0k0u5mEtzN9kwHdGrbQBwcwS9T8IO71vVdqbc7iY2vIod1-T2HOVXDvR_Iq72aGRxP53a?key=EcI-pi8eK7KHXtGxrQrIfA)

2.  Ingresar a la instancia desde la IP Elástica:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfJhsq5I55EhVJnmWpONHYagy4AR2ATOehDQJO4LnZgJRxdbKe70ArUHcMgTDa-Vt5KvzwBOlUbgp6vtPrx86bCrnK9s7DLuMe-VoplRoV4vMHGhz2pWaSz-Gq1KM3zKuUvhHE-ysNtFtP0-JfVXpP_5uiU?key=EcI-pi8eK7KHXtGxrQrIfA)
