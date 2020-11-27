---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 6590c5188e4e1758987a75fbd007099703ea6bc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250420"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="bb56d-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bb56d-102">MsmqTransportBindingElement</span></span>

<span data-ttu-id="bb56d-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bb56d-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb56d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bb56d-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bb56d-105">方法</span><span class="sxs-lookup"><span data-stu-id="bb56d-105">Methods</span></span>  

 <span data-ttu-id="bb56d-106">MsmqTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="bb56d-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bb56d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bb56d-107">Properties</span></span>  

 <span data-ttu-id="bb56d-108">MsmqTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="bb56d-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="bb56d-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="bb56d-109">MaxPoolSize</span></span>  

 <span data-ttu-id="bb56d-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="bb56d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="bb56d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bb56d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb56d-112">包含內部 MSMQ 訊息物件之集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="bb56d-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="bb56d-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="bb56d-113">QueueTransferProtocol</span></span>  

 <span data-ttu-id="bb56d-114">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="bb56d-114">Data type: string</span></span>  
  
 <span data-ttu-id="bb56d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bb56d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb56d-116">代表此繫結使用之已佇列通訊通道傳輸的列舉值。</span><span class="sxs-lookup"><span data-stu-id="bb56d-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="bb56d-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="bb56d-117">UseActiveDirectory</span></span>  

 <span data-ttu-id="bb56d-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="bb56d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="bb56d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bb56d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bb56d-120">傳回布林值，這個值會指出是否應該使用 Active Directory 來轉換佇列位址。</span><span class="sxs-lookup"><span data-stu-id="bb56d-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb56d-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="bb56d-121">Requirements</span></span>  
  
|<span data-ttu-id="bb56d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="bb56d-122">MOF</span></span>|<span data-ttu-id="bb56d-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="bb56d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bb56d-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="bb56d-124">Namespace</span></span>|<span data-ttu-id="bb56d-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="bb56d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb56d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb56d-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
