---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c2c5d54050216c91a318a407341c4ffb9cb687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="55b72-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="55b72-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="55b72-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="55b72-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b72-104">語法</span><span class="sxs-lookup"><span data-stu-id="55b72-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="55b72-105">方法</span><span class="sxs-lookup"><span data-stu-id="55b72-105">Methods</span></span>  
 <span data-ttu-id="55b72-106">MsmqTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="55b72-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="55b72-107">屬性</span><span class="sxs-lookup"><span data-stu-id="55b72-107">Properties</span></span>  
 <span data-ttu-id="55b72-108">MsmqTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="55b72-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="55b72-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="55b72-109">MaxPoolSize</span></span>  
 <span data-ttu-id="55b72-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="55b72-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="55b72-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="55b72-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55b72-112">包含內部 MSMQ 訊息物件之集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="55b72-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="55b72-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="55b72-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="55b72-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="55b72-114">Data type: string</span></span>  
  
 <span data-ttu-id="55b72-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="55b72-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55b72-116">代表此繫結使用之已佇列通訊通道傳輸的列舉值。</span><span class="sxs-lookup"><span data-stu-id="55b72-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="55b72-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="55b72-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="55b72-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="55b72-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="55b72-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="55b72-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55b72-120">傳回布林值，這個值會指出是否應該使用 Active Directory 來轉換佇列位址。</span><span class="sxs-lookup"><span data-stu-id="55b72-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55b72-121">需求</span><span class="sxs-lookup"><span data-stu-id="55b72-121">Requirements</span></span>  
  
|<span data-ttu-id="55b72-122">MOF</span><span class="sxs-lookup"><span data-stu-id="55b72-122">MOF</span></span>|<span data-ttu-id="55b72-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="55b72-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="55b72-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="55b72-124">Namespace</span></span>|<span data-ttu-id="55b72-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="55b72-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55b72-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55b72-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
