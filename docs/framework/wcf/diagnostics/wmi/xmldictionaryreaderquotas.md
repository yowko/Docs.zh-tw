---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044225"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="43d7d-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="43d7d-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="43d7d-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="43d7d-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d7d-104">語法</span><span class="sxs-lookup"><span data-stu-id="43d7d-104">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="43d7d-105">方法</span><span class="sxs-lookup"><span data-stu-id="43d7d-105">Methods</span></span>  
 <span data-ttu-id="43d7d-106">XmlDictionaryReaderQuotas 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="43d7d-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="43d7d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="43d7d-107">Properties</span></span>  
 <span data-ttu-id="43d7d-108">XmlDictionaryReaderQuotas 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="43d7d-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="43d7d-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="43d7d-109">MaxArrayLength</span></span>  
 <span data-ttu-id="43d7d-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="43d7d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="43d7d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="43d7d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43d7d-112">允許的陣列長度上限。</span><span class="sxs-lookup"><span data-stu-id="43d7d-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="43d7d-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="43d7d-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="43d7d-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="43d7d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="43d7d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="43d7d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43d7d-116">允許每個讀取動作傳回的位元組上限。</span><span class="sxs-lookup"><span data-stu-id="43d7d-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="43d7d-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="43d7d-117">MaxDepth</span></span>  
 <span data-ttu-id="43d7d-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="43d7d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="43d7d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="43d7d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43d7d-120">每個讀取動作的巢狀節點深度上限。</span><span class="sxs-lookup"><span data-stu-id="43d7d-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="43d7d-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="43d7d-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="43d7d-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="43d7d-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="43d7d-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="43d7d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43d7d-124">資料表名稱允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="43d7d-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="43d7d-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="43d7d-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="43d7d-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="43d7d-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="43d7d-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="43d7d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43d7d-128">XML 項目內容允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="43d7d-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d7d-129">需求</span><span class="sxs-lookup"><span data-stu-id="43d7d-129">Requirements</span></span>  
  
|<span data-ttu-id="43d7d-130">MOF</span><span class="sxs-lookup"><span data-stu-id="43d7d-130">MOF</span></span>|<span data-ttu-id="43d7d-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="43d7d-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="43d7d-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="43d7d-132">Namespace</span></span>|<span data-ttu-id="43d7d-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="43d7d-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43d7d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d7d-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
