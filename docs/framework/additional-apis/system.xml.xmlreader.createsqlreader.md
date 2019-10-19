---
title: XmlReader. CreateSqlReader 方法（system.string）
author: mairaw
ms.author: mairaw
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 302be4eff32d2c96a1571d291e0b289e77694db8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584131"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="93640-102">XmlReader. CreateSqlReader 方法</span><span class="sxs-lookup"><span data-stu-id="93640-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="93640-103">使用剖析用的指定資料流、設定和內容資訊，建立新的 <xref:System.Xml.XmlReader> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="93640-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input, 
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="93640-104">參數</span><span class="sxs-lookup"><span data-stu-id="93640-104">Parameters</span></span>

- <span data-ttu-id="93640-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="93640-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="93640-106">包含 XML 資料的資料流。</span><span class="sxs-lookup"><span data-stu-id="93640-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="93640-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="93640-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="93640-108">新 <xref:System.Xml.XmlReader> 執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="93640-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="93640-109">這個值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="93640-109">This value can be `null`.</span></span>

- <span data-ttu-id="93640-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="93640-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="93640-111">剖析 XML 片段所需的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="93640-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="93640-112">這個值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="93640-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="93640-113">Returns</span><span class="sxs-lookup"><span data-stu-id="93640-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="93640-114">用以在資料流中讀取 XML 資料的物件。</span><span class="sxs-lookup"><span data-stu-id="93640-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="93640-115">備註</span><span class="sxs-lookup"><span data-stu-id="93640-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="93640-116">@No__t_0 方法是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="93640-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="93640-117">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="93640-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="93640-118">需求</span><span class="sxs-lookup"><span data-stu-id="93640-118">Requirements</span></span>

<span data-ttu-id="93640-119">**命名空間︰** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="93640-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="93640-120">**元件：** .Xml .dll</span><span class="sxs-lookup"><span data-stu-id="93640-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="93640-121">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="93640-121">**.NET Framework versions:** Available since 2.0.</span></span>
