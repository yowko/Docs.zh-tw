---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149701"
---
# <a name="binding"></a><span data-ttu-id="f79fb-102">繫結</span><span class="sxs-lookup"><span data-stu-id="f79fb-102">Binding</span></span>
<span data-ttu-id="f79fb-103">wmi 繫結</span><span class="sxs-lookup"><span data-stu-id="f79fb-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="f79fb-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="f79fb-105">方法</span><span class="sxs-lookup"><span data-stu-id="f79fb-105">Methods</span></span>  
 <span data-ttu-id="f79fb-106">Binding 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f79fb-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f79fb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f79fb-107">Properties</span></span>  
 <span data-ttu-id="f79fb-108">Binding 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="f79fb-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="f79fb-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="f79fb-109">BindingElements</span></span>  
 <span data-ttu-id="f79fb-110">資料類型：BindingElement 陣列</span><span class="sxs-lookup"><span data-stu-id="f79fb-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="f79fb-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-112">此繫結類別所實作之繫結項目的集合。</span><span class="sxs-lookup"><span data-stu-id="f79fb-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="f79fb-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="f79fb-113">CloseTimeout</span></span>  
 <span data-ttu-id="f79fb-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f79fb-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="f79fb-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-116">供關閉作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f79fb-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f79fb-117">名稱</span><span class="sxs-lookup"><span data-stu-id="f79fb-117">Name</span></span>  
 <span data-ttu-id="f79fb-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f79fb-118">Data type: string</span></span>  
  
 <span data-ttu-id="f79fb-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-120">繫結的名稱。</span><span class="sxs-lookup"><span data-stu-id="f79fb-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="f79fb-121">命名空間</span><span class="sxs-lookup"><span data-stu-id="f79fb-121">Namespace</span></span>  
 <span data-ttu-id="f79fb-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f79fb-122">Data type: string</span></span>  
  
 <span data-ttu-id="f79fb-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-124">繫結的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="f79fb-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="f79fb-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="f79fb-125">OpenTimeout</span></span>  
 <span data-ttu-id="f79fb-126">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f79fb-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="f79fb-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-128">供開啟作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f79fb-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="f79fb-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f79fb-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="f79fb-130">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f79fb-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="f79fb-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-132">供接收作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f79fb-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="f79fb-133">配置</span><span class="sxs-lookup"><span data-stu-id="f79fb-133">Scheme</span></span>  
 <span data-ttu-id="f79fb-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f79fb-134">Data type: string</span></span>  
  
 <span data-ttu-id="f79fb-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-136">繫結建立之通道與接聽項處理站所使用的 URI 傳輸配置。</span><span class="sxs-lookup"><span data-stu-id="f79fb-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="f79fb-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="f79fb-137">SendTimeout</span></span>  
 <span data-ttu-id="f79fb-138">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f79fb-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="f79fb-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f79fb-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79fb-140">針對完成傳送作業所提供的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f79fb-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79fb-141">需求</span><span class="sxs-lookup"><span data-stu-id="f79fb-141">Requirements</span></span>  
  
|<span data-ttu-id="f79fb-142">MOF</span><span class="sxs-lookup"><span data-stu-id="f79fb-142">MOF</span></span>|<span data-ttu-id="f79fb-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f79fb-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f79fb-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="f79fb-144">Namespace</span></span>|<span data-ttu-id="f79fb-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f79fb-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f79fb-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f79fb-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
