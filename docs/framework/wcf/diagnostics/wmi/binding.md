---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198885"
---
# <a name="binding"></a><span data-ttu-id="56044-102">繫結</span><span class="sxs-lookup"><span data-stu-id="56044-102">Binding</span></span>
<span data-ttu-id="56044-103">wmi 繫結</span><span class="sxs-lookup"><span data-stu-id="56044-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56044-104">語法</span><span class="sxs-lookup"><span data-stu-id="56044-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="56044-105">方法</span><span class="sxs-lookup"><span data-stu-id="56044-105">Methods</span></span>  
 <span data-ttu-id="56044-106">Binding 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="56044-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="56044-107">屬性</span><span class="sxs-lookup"><span data-stu-id="56044-107">Properties</span></span>  
 <span data-ttu-id="56044-108">Binding 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="56044-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="56044-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="56044-109">BindingElements</span></span>  
 <span data-ttu-id="56044-110">資料型別：BindingElement 陣列</span><span class="sxs-lookup"><span data-stu-id="56044-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="56044-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-112">此繫結類別所實作之繫結項目的集合。</span><span class="sxs-lookup"><span data-stu-id="56044-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="56044-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="56044-113">CloseTimeout</span></span>  
 <span data-ttu-id="56044-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="56044-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="56044-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-116">供關閉作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="56044-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="56044-117">名稱</span><span class="sxs-lookup"><span data-stu-id="56044-117">Name</span></span>  
 <span data-ttu-id="56044-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="56044-118">Data type: string</span></span>  
  
 <span data-ttu-id="56044-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-120">繫結的名稱。</span><span class="sxs-lookup"><span data-stu-id="56044-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="56044-121">命名空間</span><span class="sxs-lookup"><span data-stu-id="56044-121">Namespace</span></span>  
 <span data-ttu-id="56044-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="56044-122">Data type: string</span></span>  
  
 <span data-ttu-id="56044-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-124">繫結的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="56044-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="56044-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="56044-125">OpenTimeout</span></span>  
 <span data-ttu-id="56044-126">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="56044-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="56044-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-128">供開啟作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="56044-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="56044-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="56044-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="56044-130">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="56044-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="56044-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-132">供接收作業完成其作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="56044-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="56044-133">配置</span><span class="sxs-lookup"><span data-stu-id="56044-133">Scheme</span></span>  
 <span data-ttu-id="56044-134">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="56044-134">Data type: string</span></span>  
  
 <span data-ttu-id="56044-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-136">繫結建立之通道與接聽項處理站所使用的 URI 傳輸配置。</span><span class="sxs-lookup"><span data-stu-id="56044-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="56044-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="56044-137">SendTimeout</span></span>  
 <span data-ttu-id="56044-138">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="56044-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="56044-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="56044-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56044-140">針對完成傳送作業所提供的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="56044-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56044-141">需求</span><span class="sxs-lookup"><span data-stu-id="56044-141">Requirements</span></span>  
  
|<span data-ttu-id="56044-142">MOF</span><span class="sxs-lookup"><span data-stu-id="56044-142">MOF</span></span>|<span data-ttu-id="56044-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="56044-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="56044-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="56044-144">Namespace</span></span>|<span data-ttu-id="56044-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="56044-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56044-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56044-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
