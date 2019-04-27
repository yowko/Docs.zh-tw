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
ms.openlocfilehash: d5dd2829a9a00f869af3d7f370f99361979b8106
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921312"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="1cc68-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法</span><span class="sxs-lookup"><span data-stu-id="1cc68-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="1cc68-103">[在 .NET Framework 4.5.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="1cc68-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="1cc68-104">將指定的資料流轉換為隨機存取資料流。</span><span class="sxs-lookup"><span data-stu-id="1cc68-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="1cc68-105">**命名空間：**<xref:System.IO?displayProperty=nameWithType>
**組件：** System.Runtime.WindowsRuntime （在 system.runtime.windowsruntime.dll 中）</span><span class="sxs-lookup"><span data-stu-id="1cc68-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="1cc68-106">語法</span><span class="sxs-lookup"><span data-stu-id="1cc68-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="1cc68-107">參數</span><span class="sxs-lookup"><span data-stu-id="1cc68-107">Parameters</span></span>

`stream`

<span data-ttu-id="1cc68-108">類型：<xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1cc68-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="1cc68-109">要轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="1cc68-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="1cc68-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1cc68-110">Return Value</span></span>

<span data-ttu-id="1cc68-111">類型：<xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="1cc68-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="1cc68-112">A[!INCLUDE[wrt](../../../includes/wrt-md.md)]隨機存取資料流，表示已轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="1cc68-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="1cc68-113">例外狀況</span><span class="sxs-lookup"><span data-stu-id="1cc68-113">Exceptions</span></span>

|<span data-ttu-id="1cc68-114">例外</span><span class="sxs-lookup"><span data-stu-id="1cc68-114">Exception</span></span>|<span data-ttu-id="1cc68-115">條件</span><span class="sxs-lookup"><span data-stu-id="1cc68-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="1cc68-116">要轉換的資料流不支援搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="1cc68-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1cc68-117">備註</span><span class="sxs-lookup"><span data-stu-id="1cc68-117">Remarks</span></span>

<span data-ttu-id="1cc68-118">只有在您開發 Windows 市集應用程式時，這個擴充方法才可供使用。</span><span class="sxs-lookup"><span data-stu-id="1cc68-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="1cc68-119">這個方法會提供方便處理 Windows 市集應用程式中資料流的方式。</span><span class="sxs-lookup"><span data-stu-id="1cc68-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="1cc68-120">您想要轉換的 .NET Framework 資料流必須支援搜尋。</span><span class="sxs-lookup"><span data-stu-id="1cc68-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="1cc68-121">如需詳細資訊，請參閱 <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1cc68-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cc68-122">.NET Framework 4.5.1 (含) 以後版本可支援這個 API，但 4.5 版不支援。</span><span class="sxs-lookup"><span data-stu-id="1cc68-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="1cc68-123">版本資訊</span><span class="sxs-lookup"><span data-stu-id="1cc68-123">Version Information</span></span>

<span data-ttu-id="1cc68-124">**適用於 Windows 市集應用程式的.NET**</span><span class="sxs-lookup"><span data-stu-id="1cc68-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="1cc68-125">支援於：Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="1cc68-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="1cc68-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cc68-126">See also</span></span>

- [<span data-ttu-id="1cc68-127">如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換</span><span class="sxs-lookup"><span data-stu-id="1cc68-127">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
