---
title: 記錄類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990335"
---
# <a name="logging-class"></a>Logging 類別

提供追蹤記錄功能。

```csharp
internal class Logging
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="associate-method"></a>關聯方法

記錄兩個物件彼此關聯的資訊。

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `objA` <xref:System.Object>

  要與相關聯的物件 `objB` 。

- `objB` <xref:System.Object>

  要與相關聯的物件 `objA` 。

## <a name="entertracesource-object-string-string-method"></a>輸入（TraceSource、object、string、string）方法

將進入方法的記錄檔。

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.Object>

  呼叫方法的物件。

- `method` <xref:System.String>

  要輸入的方法。

- `param` <xref:System.String>

  傳遞給方法的參數。

## <a name="entertracesource-object-string-object-method"></a>輸入（TraceSource、object、string、object）方法

將進入方法的記錄檔。

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.Object>

  呼叫方法的物件。

- `method` <xref:System.String>

  要輸入的方法。

- `paramObject` <xref:System.Object>

  傳遞給方法的參數。

## <a name="entertracesource-string-string-string-method"></a>Enter （TraceSource，string，string，string）方法

將進入方法的記錄檔。

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.String>

  呼叫方法的物件。

- `method` <xref:System.String>

  要輸入的方法。

- `param` <xref:System.String>

  傳遞給方法的參數。

## <a name="entertracesource-string-string-object-method"></a>輸入（TraceSource、string、string、object）方法

將進入方法的記錄檔。

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.String>

  呼叫方法的物件。

- `method` <xref:System.String>

  要輸入的方法。

- `paramObject` <xref:System.Object>

  傳遞給方法的參數。

## <a name="entertracesource-string-string-method"></a>輸入（TraceSource，string，string）方法

將進入方法的記錄檔。

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `method` <xref:System.String>

  要輸入的方法。

- `parameters` <xref:System.String>

  傳遞給方法的參數。

## <a name="entertracesource-string-method"></a>輸入（TraceSource，string）方法

將進入方法的記錄檔。

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `msg` <xref:System.String>

  要記錄至追蹤來源的進入訊息。

## <a name="exception-method"></a>Exception 方法

記錄例外狀況並還原縮排。

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.Object>

  在上呼叫擲回例外狀況之方法的物件。

- `method` <xref:System.String>

  擲回例外狀況的方法。

- `e` <xref:System.Exception>

  已擲回的例外狀況。

## <a name="exittracesource-object-string-object-method"></a>Exit （TraceSource、object、string、object）方法

記錄結束于函式。

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.Object>

  呼叫方法的物件。

- `method` <xref:System.String>

  即將結束的方法。

- `retObject` <xref:System.Object>

  方法所傳回的值。

## <a name="exittracesource-string-string-object-method"></a>Exit （TraceSource，string，string，object）方法

記錄結束于函式。

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.String>

  呼叫方法的物件。

- `method` <xref:System.String>

  即將結束的方法。

- `retObject` <xref:System.Object>

  方法所傳回的值。

## <a name="exittracesource-object-string-string-method"></a>Exit （TraceSource，object，string，string）方法

記錄結束于函式。

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.Object>

  呼叫方法的物件。

- `method` <xref:System.String>

  即將結束的方法。

- `retValue` <xref:System.String>

  方法所傳回的值。

## <a name="exittracesource-string-string-string-method"></a>Exit （TraceSource，string，string，string）方法

記錄結束于函式。

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `obj` <xref:System.String>

  呼叫方法的物件。

- `method` <xref:System.String>

  即將結束的方法。

- `retValue` <xref:System.String>

  方法所傳回的值。

## <a name="exittracesource-string-string-method"></a>Exit （TraceSource，string，string）方法

記錄結束于函式。

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `method` <xref:System.String>

  即將結束的方法。

- `parameters` <xref:System.String>

  傳遞至即將結束之方法的參數。

## <a name="exittracesource-string-method"></a>Exit （TraceSource，string）方法

記錄結束于函式。

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>參數

- `traceSource` <xref:System.Diagnostics.TraceSource>

  要記錄事件的追蹤來源。

- `msg` <xref:System.String>

  要記錄到追蹤來源的結束訊息。

## <a name="http-property"></a>Http 屬性

取得 "System .Net. Http" 的追蹤來源。

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a>屬性值

<xref:System.Diagnostics.TraceSource>\
"System .Net. Http" 的追蹤來源， `null` 如果未啟用記錄，則為。

## <a name="on-property"></a>On 屬性

取得值，這個值表示是否啟用記錄。

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a>屬性值

<xref:System.Boolean>\
如果已啟用記錄，則為 `true`，否則為 `false`。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
