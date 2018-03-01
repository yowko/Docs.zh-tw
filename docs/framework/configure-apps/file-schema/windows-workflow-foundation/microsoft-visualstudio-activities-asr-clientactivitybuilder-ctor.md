---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4c50d9754b71386e6809d46cd9666987a704fbf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="d7b9f-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="d7b9f-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="d7b9f-103">建立的執行個體[Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)類別。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b9f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7b9f-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7b9f-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7b9f-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="d7b9f-106">參數值</span><span class="sxs-lookup"><span data-stu-id="d7b9f-106">Parameter Values</span></span>  
 <span data-ttu-id="d7b9f-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="d7b9f-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="d7b9f-108">描述要在產生之工作流程活動中執行的作業，包括作業名稱、傳回型別和參數資訊。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="d7b9f-109">這個參數的值不能**null**。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="d7b9f-110">它應描述會使用訊息合約並接收含有一則訊息之引數的同步作業。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="d7b9f-111">如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="d7b9f-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="d7b9f-112">*configurationName*</span></span>  
  
 <span data-ttu-id="d7b9f-113">指定端點組態名稱。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="d7b9f-114">這個參數的值不能是**null**或空白。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="d7b9f-115">如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="d7b9f-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="d7b9f-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="d7b9f-117">指定作業的服務命名空間。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="d7b9f-118">這個參數的值不能是**null**或空白。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="d7b9f-119">如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。</span><span class="sxs-lookup"><span data-stu-id="d7b9f-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b9f-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b9f-120">See Also</span></span>  
 [<span data-ttu-id="d7b9f-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="d7b9f-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
