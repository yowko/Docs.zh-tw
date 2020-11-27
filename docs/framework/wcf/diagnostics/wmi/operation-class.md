---
title: 作業類別
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 6b47d933dc84813532398830c92c95210208a709
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269154"
---
# <a name="operation-class"></a><span data-ttu-id="9fd0a-102">作業類別</span><span class="sxs-lookup"><span data-stu-id="9fd0a-102">Operation class</span></span>

<span data-ttu-id="9fd0a-103">作業</span><span class="sxs-lookup"><span data-stu-id="9fd0a-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd0a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9fd0a-104">Syntax</span></span>  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9fd0a-105">方法</span><span class="sxs-lookup"><span data-stu-id="9fd0a-105">Methods</span></span>  

 <span data-ttu-id="9fd0a-106">Operation 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9fd0a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9fd0a-107">Properties</span></span>  

 <span data-ttu-id="9fd0a-108">Operation 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="9fd0a-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="9fd0a-109">動作</span><span class="sxs-lookup"><span data-stu-id="9fd0a-109">Action</span></span>  

 <span data-ttu-id="9fd0a-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="9fd0a-110">Data type: string</span></span>  
  
 <span data-ttu-id="9fd0a-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-112">要求訊息的 WS-Addressing 動作。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="9fd0a-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="9fd0a-113">AsyncPattern</span></span>  

 <span data-ttu-id="9fd0a-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="9fd0a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="9fd0a-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-116">表示 `Begin` 在服務合約中使用 [開放式/右角括弧] 和 `End` [開啟/關閉角括弧] 方法組，以非同步方式執行作業。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="9fd0a-117">行為</span><span class="sxs-lookup"><span data-stu-id="9fd0a-117">Behaviors</span></span>  

 <span data-ttu-id="9fd0a-118">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="9fd0a-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="9fd0a-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-120">與這個作業有關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="9fd0a-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="9fd0a-121">IsCallback</span></span>  

 <span data-ttu-id="9fd0a-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="9fd0a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="9fd0a-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-124">當作業是回呼作業時為 True。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="9fd0a-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="9fd0a-125">IsInitiating</span></span>  

 <span data-ttu-id="9fd0a-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="9fd0a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="9fd0a-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-128">代表方法是否實作可在伺服器上初始化工作階段的作業。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="9fd0a-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="9fd0a-129">IsOneWay</span></span>  

 <span data-ttu-id="9fd0a-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="9fd0a-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="9fd0a-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-132">代表作業是否傳回回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="9fd0a-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="9fd0a-133">IsTerminating</span></span>  

 <span data-ttu-id="9fd0a-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="9fd0a-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="9fd0a-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-136">代表作業是否傳回回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="9fd0a-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="9fd0a-137">MethodSignature</span></span>  

 <span data-ttu-id="9fd0a-138">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="9fd0a-138">Data type: string</span></span>  
  
 <span data-ttu-id="9fd0a-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-140">作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9fd0a-141">Name</span><span class="sxs-lookup"><span data-stu-id="9fd0a-141">Name</span></span>  

 <span data-ttu-id="9fd0a-142">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="9fd0a-142">Data type: string</span></span>  
  
 <span data-ttu-id="9fd0a-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-144">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="9fd0a-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="9fd0a-145">ParameterTypes</span></span>  

 <span data-ttu-id="9fd0a-146">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="9fd0a-146">Data type: string array</span></span>  
  
 <span data-ttu-id="9fd0a-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-148">作業的參數類型。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="9fd0a-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="9fd0a-149">ReplyAction</span></span>  

 <span data-ttu-id="9fd0a-150">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="9fd0a-150">Data type: string</span></span>  
  
 <span data-ttu-id="9fd0a-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-152">作業的回覆訊息的 SOAP 動作值。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="9fd0a-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="9fd0a-153">ReturnType</span></span>  

 <span data-ttu-id="9fd0a-154">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="9fd0a-154">Data type: string</span></span>  
  
 <span data-ttu-id="9fd0a-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9fd0a-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fd0a-156">作業的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fd0a-157">規格需求</span><span class="sxs-lookup"><span data-stu-id="9fd0a-157">Requirements</span></span>  
  
|<span data-ttu-id="9fd0a-158">MOF</span><span class="sxs-lookup"><span data-stu-id="9fd0a-158">MOF</span></span>|<span data-ttu-id="9fd0a-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="9fd0a-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9fd0a-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="9fd0a-160">Namespace</span></span>|<span data-ttu-id="9fd0a-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="9fd0a-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fd0a-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fd0a-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
