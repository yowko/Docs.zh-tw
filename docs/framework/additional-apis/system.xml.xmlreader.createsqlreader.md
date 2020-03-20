---
title: XmlReader.createSqlReader 方法（系統.Xml）
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 7bd2ef5158516acede47f73f9937d06159bc16c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155735"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="69103-102">XmlReader.CreateSqlReader 方法</span><span class="sxs-lookup"><span data-stu-id="69103-102">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="69103-103">使用剖析用的指定資料流、設定和內容資訊，建立新的 <xref:System.Xml.XmlReader> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="69103-103">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="69103-104">參數</span><span class="sxs-lookup"><span data-stu-id="69103-104">Parameters</span></span>

- <span data-ttu-id="69103-105">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="69103-105">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="69103-106">包含 XML 資料的資料流。</span><span class="sxs-lookup"><span data-stu-id="69103-106">The stream that contains the XML data.</span></span>

- <span data-ttu-id="69103-107">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="69103-107">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="69103-108">新 <xref:System.Xml.XmlReader> 執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="69103-108">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="69103-109">此值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="69103-109">This value can be `null`.</span></span>

- <span data-ttu-id="69103-110">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="69103-110">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="69103-111">剖析 XML 片段所需的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="69103-111">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="69103-112">此值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="69103-112">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="69103-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="69103-113">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="69103-114">用以在資料流中讀取 XML 資料的物件。</span><span class="sxs-lookup"><span data-stu-id="69103-114">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="69103-115">備註</span><span class="sxs-lookup"><span data-stu-id="69103-115">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="69103-116">該方法`XmlReader.CreateSqlReader`是內部的，不用於直接在代碼中使用。</span><span class="sxs-lookup"><span data-stu-id="69103-116">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="69103-117">在任何情況下，Microsoft 都不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="69103-117">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="69103-118">需求</span><span class="sxs-lookup"><span data-stu-id="69103-118">Requirements</span></span>

<span data-ttu-id="69103-119">**命名空間：**<xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="69103-119">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="69103-120">**裝配：** 系統.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="69103-120">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="69103-121">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="69103-121">**.NET Framework versions:** Available since 2.0.</span></span>
