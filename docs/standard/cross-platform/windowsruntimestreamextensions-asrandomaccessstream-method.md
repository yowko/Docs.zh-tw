---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9057eabb7e3dfdfaa872fbcf2fe1180d0bbc7920
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="ae41d-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) 方法</span><span class="sxs-lookup"><span data-stu-id="ae41d-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="ae41d-103">[在 .NET Framework 4.5.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="ae41d-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="ae41d-104">將指定的資料流轉換為隨機存取資料流。</span><span class="sxs-lookup"><span data-stu-id="ae41d-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="ae41d-105">**命名空間：**<xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ae41d-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="ae41d-106">**組件：** System.Runtime.WindowsRuntime （在 system.runtime.windowsruntime.dll 中）</span><span class="sxs-lookup"><span data-stu-id="ae41d-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae41d-107">語法</span><span class="sxs-lookup"><span data-stu-id="ae41d-107">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ae41d-108">參數</span><span class="sxs-lookup"><span data-stu-id="ae41d-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="ae41d-109">類型：<xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ae41d-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="ae41d-110">要轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="ae41d-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae41d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae41d-111">Return Value</span></span>  
 <span data-ttu-id="ae41d-112">類型： [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="ae41d-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="ae41d-113">A[!INCLUDE[wrt](../../../includes/wrt-md.md)]隨機存取資料流，表示已轉換的資料流。</span><span class="sxs-lookup"><span data-stu-id="ae41d-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="ae41d-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ae41d-114">Exceptions</span></span>  
  
|<span data-ttu-id="ae41d-115">例外</span><span class="sxs-lookup"><span data-stu-id="ae41d-115">Exception</span></span>|<span data-ttu-id="ae41d-116">條件</span><span class="sxs-lookup"><span data-stu-id="ae41d-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="ae41d-117">要轉換的資料流不支援搜尋功能。</span><span class="sxs-lookup"><span data-stu-id="ae41d-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae41d-118">備註</span><span class="sxs-lookup"><span data-stu-id="ae41d-118">Remarks</span></span>  
 <span data-ttu-id="ae41d-119">只有在您開發 Windows 市集應用程式時，這個擴充方法才可供使用。</span><span class="sxs-lookup"><span data-stu-id="ae41d-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="ae41d-120">這個方法會提供方便處理 Windows 市集應用程式中資料流的方式。</span><span class="sxs-lookup"><span data-stu-id="ae41d-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="ae41d-121">您想要轉換的 .NET Framework 資料流必須支援搜尋。</span><span class="sxs-lookup"><span data-stu-id="ae41d-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="ae41d-122">如需詳細資訊，請參閱 <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ae41d-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae41d-123">.NET Framework 4.5.1 (含) 以後版本可支援這個 API，但 4.5 版不支援。</span><span class="sxs-lookup"><span data-stu-id="ae41d-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="ae41d-124">版本資訊</span><span class="sxs-lookup"><span data-stu-id="ae41d-124">Version Information</span></span>  
 <span data-ttu-id="ae41d-125">**適用於 Windows 市集應用程式的.NET**</span><span class="sxs-lookup"><span data-stu-id="ae41d-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="ae41d-126">支援：Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ae41d-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae41d-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae41d-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="ae41d-128">操作說明：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換</span><span class="sxs-lookup"><span data-stu-id="ae41d-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
