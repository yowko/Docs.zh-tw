---
title: WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8935a8c282bbe812ad76ac6d4228c38ab12626a4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193584"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法

[在 .NET Framework 4.5.1 及更新版本中支援]

將指定的資料流轉換為隨機存取資料流。

**命名空間：** <xref:System.IO?displayProperty=nameWithType> 
**組件：** System.Runtime.WindowsRuntime （在 system.runtime.windowsruntime.dll 中）

## <a name="syntax"></a>語法

```csharp
[CLSCompliantAttribute(false)]
public static IRandomAccessStream AsRandomAccessStream(Stream stream)
```

```vb
'Declaration
<ExtensionAttribute> _
<CLSCompliantAttribute(False)> _
Public Shared Function AsRandomAccessStream ( _
        stream As Stream) As IRandomAccessStream
```

## <a name="parameters"></a>參數

`stream`

類型：<xref:System.IO.Stream?displayProperty=nameWithType>  
要轉換的資料流。

## <a name="return-value"></a>傳回值

類型：<xref:Windows.Storage.Streams.RandomAccessStream>  
A[!INCLUDE[wrt](../../../includes/wrt-md.md)]隨機存取資料流，表示已轉換的資料流。

## <a name="exceptions"></a>例外狀況

|例外|條件|
|---------------|---------------|
|<xref:System.NotSupportedException>|要轉換的資料流不支援搜尋功能。|

## <a name="remarks"></a>備註

只有在您開發 Windows 市集應用程式時，這個擴充方法才可供使用。 這個方法會提供方便處理 Windows 市集應用程式中資料流的方式。 您想要轉換的 .NET Framework 資料流必須支援搜尋。 如需詳細資訊，請參閱 <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> 方法。

> [!IMPORTANT]
> .NET Framework 4.5.1 (含) 以後版本可支援這個 API，但 4.5 版不支援。

## <a name="version-information"></a>版本資訊

**適用於 Windows 市集應用程式的.NET**

支援：Windows 8.1

## <a name="see-also"></a>另請參閱

-[System.io.windowsruntimestreamextensions （英文)](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[How to:.NET Framework 資料流與 Windows 執行階段資料流之間轉換](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
