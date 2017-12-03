---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c0ff11752ae1030e574182cfb825fb87ddc8c7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="64eda-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="64eda-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="64eda-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="64eda-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64eda-104">語法</span><span class="sxs-lookup"><span data-stu-id="64eda-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="64eda-105">方法</span><span class="sxs-lookup"><span data-stu-id="64eda-105">Methods</span></span>  
 <span data-ttu-id="64eda-106">XmlDictionaryReaderQuotas 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="64eda-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="64eda-107">屬性</span><span class="sxs-lookup"><span data-stu-id="64eda-107">Properties</span></span>  
 <span data-ttu-id="64eda-108">XmlDictionaryReaderQuotas 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="64eda-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="64eda-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="64eda-109">MaxArrayLength</span></span>  
 <span data-ttu-id="64eda-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="64eda-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="64eda-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="64eda-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="64eda-112">允許的陣列長度上限。</span><span class="sxs-lookup"><span data-stu-id="64eda-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="64eda-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="64eda-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="64eda-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="64eda-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="64eda-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="64eda-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="64eda-116">允許每個讀取動作傳回的位元組上限。</span><span class="sxs-lookup"><span data-stu-id="64eda-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="64eda-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="64eda-117">MaxDepth</span></span>  
 <span data-ttu-id="64eda-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="64eda-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="64eda-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="64eda-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="64eda-120">每個讀取動作的巢狀節點深度上限。</span><span class="sxs-lookup"><span data-stu-id="64eda-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="64eda-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="64eda-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="64eda-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="64eda-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="64eda-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="64eda-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="64eda-124">資料表名稱允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="64eda-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="64eda-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="64eda-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="64eda-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="64eda-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="64eda-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="64eda-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="64eda-128">XML 項目內容允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="64eda-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64eda-129">需求</span><span class="sxs-lookup"><span data-stu-id="64eda-129">Requirements</span></span>  
  
|<span data-ttu-id="64eda-130">MOF</span><span class="sxs-lookup"><span data-stu-id="64eda-130">MOF</span></span>|<span data-ttu-id="64eda-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="64eda-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="64eda-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="64eda-132">Namespace</span></span>|<span data-ttu-id="64eda-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="64eda-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64eda-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64eda-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
