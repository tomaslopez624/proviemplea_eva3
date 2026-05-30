# Swagger\Client\AdministracinApi

All URIs are relative to *http://localhost:8080/api*

Method | HTTP request | Description
------------- | ------------- | -------------
[**actualizarEstadoContacto**](AdministracinApi.md#actualizarestadocontacto) | **PATCH** /admin/contactos/{id}/estado | Actualizar estado de contacto
[**crearContactoSolicitado**](AdministracinApi.md#crearcontactosolicitado) | **POST** /admin/contactos | Registrar solicitud de contacto
[**getContactosSolicitados**](AdministracinApi.md#getcontactossolicitados) | **GET** /admin/contactos | Listar contactos solicitados
[**getEstadisticas**](AdministracinApi.md#getestadisticas) | **GET** /admin/estadisticas | Estadísticas generales de la plataforma

# **actualizarEstadoContacto**
> actualizarEstadoContacto($body, $id)

Actualizar estado de contacto

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AdministracinApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$body = new \Swagger\Client\Model\IdEstadoBody(); // \Swagger\Client\Model\IdEstadoBody | 
$id = "38400000-8cf0-11bd-b23e-10b96e4ef00d"; // string | 

try {
    $apiInstance->actualizarEstadoContacto($body, $id);
} catch (Exception $e) {
    echo 'Exception when calling AdministracinApi->actualizarEstadoContacto: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\Swagger\Client\Model\IdEstadoBody**](../Model/IdEstadoBody.md)|  |
 **id** | [**string**](../Model/.md)|  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **crearContactoSolicitado**
> crearContactoSolicitado($body)

Registrar solicitud de contacto

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AdministracinApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$body = new \Swagger\Client\Model\AdminContactosBody(); // \Swagger\Client\Model\AdminContactosBody | 

try {
    $apiInstance->crearContactoSolicitado($body);
} catch (Exception $e) {
    echo 'Exception when calling AdministracinApi->crearContactoSolicitado: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **body** | [**\Swagger\Client\Model\AdminContactosBody**](../Model/AdminContactosBody.md)|  |

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getContactosSolicitados**
> getContactosSolicitados($estado)

Listar contactos solicitados

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AdministracinApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);
$estado = "estado_example"; // string | 

try {
    $apiInstance->getContactosSolicitados($estado);
} catch (Exception $e) {
    echo 'Exception when calling AdministracinApi->getContactosSolicitados: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **estado** | **string**|  | [optional]

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

# **getEstadisticas**
> getEstadisticas()

Estadísticas generales de la plataforma

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

$apiInstance = new Swagger\Client\Api\AdministracinApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client()
);

try {
    $apiInstance->getEstadisticas();
} catch (Exception $e) {
    echo 'Exception when calling AdministracinApi->getEstadisticas: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters
This endpoint does not need any parameter.

### Return type

void (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: Not defined

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

