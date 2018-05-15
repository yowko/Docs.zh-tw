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
ms.openlocfilehash: 16f878abc11589fe62f78d941b367d82d7b49e1c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="7db3f-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法</span><span class="sxs-lookup"><span data-stu-id="7db3f-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="7db3f-103">[在 .NET Framework 4.5.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="7db3f-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="7db3f-104">將指定的資料流轉換為隨機存取資料流。</span><span class="sxs-lookup"><span data-stu-id="7db3f-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="7db3f-105">**命名空間：** <xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7db3f-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="7db3f-106">**組件：** System.Runtime.WindowsRuntime （在 system.runtime.windowsruntime.dll 中）</span><span class="sxs-lookup"><span data-stu-id="7db3f-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7db3f-107">語法</span><span class="sxs-lookup"><span data-stu-id="7db3f-107">Syntax</span></span>  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7db3f-108">參數</span><span class="sxs-lookup"><span data-stu-id="7db3f-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="7db3f-109">類型：<xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7db3f-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="7db3f-110">要轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="7db3f-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7db3f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7db3f-111">Return Value</span></span>  
 <span data-ttu-id="7db3f-112">類型： [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="7db3f-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="7db3f-113">A[!INCLUDE[wrt](../../../includes/wrt-md.md)]隨機存取資料流，表示已轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="7db3f-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="7db3f-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7db3f-114">Exceptions</span></span>  
  
|<span data-ttu-id="7db3f-115">例外</span><span class="sxs-lookup"><span data-stu-id="7db3f-115">Exception</span></span>|<span data-ttu-id="7db3f-116">條件</span><span class="sxs-lookup"><span data-stu-id="7db3f-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="7db3f-117">要轉換的資料流不支援搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="7db3f-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7db3f-118">備註</span><span class="sxs-lookup"><span data-stu-id="7db3f-118">Remarks</span></span>  
 <span data-ttu-id="7db3f-119">只有在您開發 Windows 市集應用程式時，這個擴充方法才可供使用。</span><span class="sxs-lookup"><span data-stu-id="7db3f-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="7db3f-120">這個方法會提供方便處理 Windows 市集應用程式中資料流的方式。</span><span class="sxs-lookup"><span data-stu-id="7db3f-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="7db3f-121">您想要轉換的 .NET Framework 資料流必須支援搜尋。</span><span class="sxs-lookup"><span data-stu-id="7db3f-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="7db3f-122">如需詳細資訊，請參閱 <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7db3f-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7db3f-123">.NET Framework 4.5.1 (含) 以後版本可支援這個 API，但 4.5 版不支援。</span><span class="sxs-lookup"><span data-stu-id="7db3f-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="7db3f-124">版本資訊</span><span class="sxs-lookup"><span data-stu-id="7db3f-124">Version Information</span></span>  
 <span data-ttu-id="7db3f-125">**適用於 Windows 市集應用程式的.NET**</span><span class="sxs-lookup"><span data-stu-id="7db3f-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="7db3f-126">支援：Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7db3f-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db3f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7db3f-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="7db3f-128">操作說明：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換</span><span class="sxs-lookup"><span data-stu-id="7db3f-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
