---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6553d1e1c030a30eed74ff81d3e07e28a9f25b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="binding"></a><span data-ttu-id="ff79d-102">繫結</span><span class="sxs-lookup"><span data-stu-id="ff79d-102">Binding</span></span>
<span data-ttu-id="ff79d-103">wmi 繫結</span><span class="sxs-lookup"><span data-stu-id="ff79d-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff79d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff79d-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ff79d-105">方法</span><span class="sxs-lookup"><span data-stu-id="ff79d-105">Methods</span></span>  
 <span data-ttu-id="ff79d-106">Binding 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ff79d-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ff79d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ff79d-107">Properties</span></span>  
 <span data-ttu-id="ff79d-108">Binding 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="ff79d-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="ff79d-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="ff79d-109">BindingElements</span></span>  
 <span data-ttu-id="ff79d-110">資料型別：BindingElement 陣列</span><span class="sxs-lookup"><span data-stu-id="ff79d-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="ff79d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-112">此繫結類別所實作之繫結項目的集合。</span><span class="sxs-lookup"><span data-stu-id="ff79d-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="ff79d-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="ff79d-113">CloseTimeout</span></span>  
 <span data-ttu-id="ff79d-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="ff79d-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="ff79d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-116">供關閉作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ff79d-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ff79d-117">名稱</span><span class="sxs-lookup"><span data-stu-id="ff79d-117">Name</span></span>  
 <span data-ttu-id="ff79d-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ff79d-118">Data type: string</span></span>  
  
 <span data-ttu-id="ff79d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-120">繫結的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff79d-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ff79d-121">命名空間</span><span class="sxs-lookup"><span data-stu-id="ff79d-121">Namespace</span></span>  
 <span data-ttu-id="ff79d-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ff79d-122">Data type: string</span></span>  
  
 <span data-ttu-id="ff79d-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-124">繫結的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ff79d-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="ff79d-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="ff79d-125">OpenTimeout</span></span>  
 <span data-ttu-id="ff79d-126">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="ff79d-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="ff79d-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-128">供開啟作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ff79d-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="ff79d-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="ff79d-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="ff79d-130">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="ff79d-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="ff79d-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-132">供接收作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ff79d-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="ff79d-133">配置</span><span class="sxs-lookup"><span data-stu-id="ff79d-133">Scheme</span></span>  
 <span data-ttu-id="ff79d-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ff79d-134">Data type: string</span></span>  
  
 <span data-ttu-id="ff79d-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-136">繫結建立之通道與接聽項處理站所使用的 URI 傳輸配置。</span><span class="sxs-lookup"><span data-stu-id="ff79d-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="ff79d-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="ff79d-137">SendTimeout</span></span>  
 <span data-ttu-id="ff79d-138">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="ff79d-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="ff79d-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff79d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff79d-140">針對完成傳送作業所提供的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="ff79d-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff79d-141">需求</span><span class="sxs-lookup"><span data-stu-id="ff79d-141">Requirements</span></span>  
  
|<span data-ttu-id="ff79d-142">MOF</span><span class="sxs-lookup"><span data-stu-id="ff79d-142">MOF</span></span>|<span data-ttu-id="ff79d-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ff79d-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ff79d-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="ff79d-144">Namespace</span></span>|<span data-ttu-id="ff79d-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="ff79d-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff79d-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="ff79d-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
