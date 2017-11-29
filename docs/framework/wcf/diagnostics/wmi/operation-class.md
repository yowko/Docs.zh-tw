---
title: "Operation 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a><span data-ttu-id="75ea8-102">Operation 類別</span><span class="sxs-lookup"><span data-stu-id="75ea8-102">Operation class</span></span>
<span data-ttu-id="75ea8-103">運算</span><span class="sxs-lookup"><span data-stu-id="75ea8-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ea8-104">語法</span><span class="sxs-lookup"><span data-stu-id="75ea8-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="75ea8-105">方法</span><span class="sxs-lookup"><span data-stu-id="75ea8-105">Methods</span></span>  
 <span data-ttu-id="75ea8-106">Operation 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="75ea8-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="75ea8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="75ea8-107">Properties</span></span>  
 <span data-ttu-id="75ea8-108">Operation 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="75ea8-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="75ea8-109">動作</span><span class="sxs-lookup"><span data-stu-id="75ea8-109">Action</span></span>  
 <span data-ttu-id="75ea8-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="75ea8-110">Data type: string</span></span>  
  
 <span data-ttu-id="75ea8-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-112">要求訊息的 WS-Addressing 動作。</span><span class="sxs-lookup"><span data-stu-id="75ea8-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="75ea8-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="75ea8-113">AsyncPattern</span></span>  
 <span data-ttu-id="75ea8-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="75ea8-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="75ea8-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-116">表示使用以非同步方式實作作業`Begin`[左右角括號] 和`End`服務合約中的 [開啟/關閉角度 brackets] 方法組。</span><span class="sxs-lookup"><span data-stu-id="75ea8-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="75ea8-117">「行為」</span><span class="sxs-lookup"><span data-stu-id="75ea8-117">Behaviors</span></span>  
 <span data-ttu-id="75ea8-118">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="75ea8-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="75ea8-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-120">與這個作業有關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="75ea8-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="75ea8-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="75ea8-121">IsCallback</span></span>  
 <span data-ttu-id="75ea8-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="75ea8-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="75ea8-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-124">當作業是回呼作業時為 True。</span><span class="sxs-lookup"><span data-stu-id="75ea8-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="75ea8-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="75ea8-125">IsInitiating</span></span>  
 <span data-ttu-id="75ea8-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="75ea8-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="75ea8-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-128">代表方法是否實作可在伺服器上初始化工作階段的作業。</span><span class="sxs-lookup"><span data-stu-id="75ea8-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="75ea8-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="75ea8-129">IsOneWay</span></span>  
 <span data-ttu-id="75ea8-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="75ea8-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="75ea8-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-132">代表作業是否傳回回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="75ea8-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="75ea8-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="75ea8-133">IsTerminating</span></span>  
 <span data-ttu-id="75ea8-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="75ea8-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="75ea8-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-136">代表作業是否傳回回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="75ea8-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="75ea8-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="75ea8-137">MethodSignature</span></span>  
 <span data-ttu-id="75ea8-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="75ea8-138">Data type: string</span></span>  
  
 <span data-ttu-id="75ea8-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-140">作業的方法簽章。</span><span class="sxs-lookup"><span data-stu-id="75ea8-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="75ea8-141">名稱</span><span class="sxs-lookup"><span data-stu-id="75ea8-141">Name</span></span>  
 <span data-ttu-id="75ea8-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="75ea8-142">Data type: string</span></span>  
  
 <span data-ttu-id="75ea8-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-144">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="75ea8-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="75ea8-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="75ea8-145">ParameterTypes</span></span>  
 <span data-ttu-id="75ea8-146">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="75ea8-146">Data type: string array</span></span>  
  
 <span data-ttu-id="75ea8-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-148">作業的參數類型。</span><span class="sxs-lookup"><span data-stu-id="75ea8-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="75ea8-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="75ea8-149">ReplyAction</span></span>  
 <span data-ttu-id="75ea8-150">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="75ea8-150">Data type: string</span></span>  
  
 <span data-ttu-id="75ea8-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-152">作業的回覆訊息的 SOAP 動作值。</span><span class="sxs-lookup"><span data-stu-id="75ea8-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="75ea8-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="75ea8-153">ReturnType</span></span>  
 <span data-ttu-id="75ea8-154">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="75ea8-154">Data type: string</span></span>  
  
 <span data-ttu-id="75ea8-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75ea8-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75ea8-156">作業的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="75ea8-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ea8-157">需求</span><span class="sxs-lookup"><span data-stu-id="75ea8-157">Requirements</span></span>  
  
|<span data-ttu-id="75ea8-158">MOF</span><span class="sxs-lookup"><span data-stu-id="75ea8-158">MOF</span></span>|<span data-ttu-id="75ea8-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="75ea8-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="75ea8-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="75ea8-160">Namespace</span></span>|<span data-ttu-id="75ea8-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="75ea8-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75ea8-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75ea8-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
