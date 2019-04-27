---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f1c12a0a60397a84d4e9ff0241c4182b4511af5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858425"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="c9e67-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c9e67-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="c9e67-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c9e67-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e67-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9e67-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="c9e67-105">方法</span><span class="sxs-lookup"><span data-stu-id="c9e67-105">Methods</span></span>  
 <span data-ttu-id="c9e67-106">XmlDictionaryReaderQuotas 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="c9e67-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c9e67-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c9e67-107">Properties</span></span>  
 <span data-ttu-id="c9e67-108">XmlDictionaryReaderQuotas 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c9e67-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="c9e67-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="c9e67-109">MaxArrayLength</span></span>  
 <span data-ttu-id="c9e67-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c9e67-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c9e67-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9e67-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9e67-112">允許的陣列長度上限。</span><span class="sxs-lookup"><span data-stu-id="c9e67-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="c9e67-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="c9e67-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="c9e67-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c9e67-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c9e67-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9e67-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9e67-116">允許每個讀取動作傳回的位元組上限。</span><span class="sxs-lookup"><span data-stu-id="c9e67-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="c9e67-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="c9e67-117">MaxDepth</span></span>  
 <span data-ttu-id="c9e67-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c9e67-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c9e67-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9e67-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9e67-120">每個讀取動作的巢狀節點深度上限。</span><span class="sxs-lookup"><span data-stu-id="c9e67-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="c9e67-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="c9e67-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="c9e67-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c9e67-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="c9e67-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9e67-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9e67-124">資料表名稱允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="c9e67-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="c9e67-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="c9e67-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="c9e67-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c9e67-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="c9e67-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c9e67-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9e67-128">XML 項目內容允許的字元數目上限。</span><span class="sxs-lookup"><span data-stu-id="c9e67-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e67-129">需求</span><span class="sxs-lookup"><span data-stu-id="c9e67-129">Requirements</span></span>  
  
|<span data-ttu-id="c9e67-130">MOF</span><span class="sxs-lookup"><span data-stu-id="c9e67-130">MOF</span></span>|<span data-ttu-id="c9e67-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="c9e67-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c9e67-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="c9e67-132">Namespace</span></span>|<span data-ttu-id="c9e67-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="c9e67-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9e67-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9e67-134">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
