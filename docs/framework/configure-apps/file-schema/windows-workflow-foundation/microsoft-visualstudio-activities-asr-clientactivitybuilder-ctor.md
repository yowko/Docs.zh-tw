---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b73274a09ae748cdf1ee33c885de86b1f52c105
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="bdbfa-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="bdbfa-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="bdbfa-103">建立的執行個體[Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)類別。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdbfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdbfa-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdbfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="bdbfa-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="bdbfa-106">參數值</span><span class="sxs-lookup"><span data-stu-id="bdbfa-106">Parameter Values</span></span>  
 <span data-ttu-id="bdbfa-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="bdbfa-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="bdbfa-108">描述要在產生之工作流程活動中執行的作業，包括作業名稱、傳回型別和參數資訊。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="bdbfa-109">這個參數的值不能**null**。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="bdbfa-110">它應描述會使用訊息合約並接收含有一則訊息之引數的同步作業。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="bdbfa-111">如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="bdbfa-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="bdbfa-112">*configurationName*</span></span>  
  
 <span data-ttu-id="bdbfa-113">指定端點組態名稱。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="bdbfa-114">這個參數的值不能是**null**或空白。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="bdbfa-115">如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="bdbfa-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="bdbfa-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="bdbfa-117">指定作業的服務命名空間。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="bdbfa-118">這個參數的值不能是**null**或空白。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="bdbfa-119">如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。</span><span class="sxs-lookup"><span data-stu-id="bdbfa-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdbfa-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdbfa-120">See Also</span></span>  
 [<span data-ttu-id="bdbfa-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="bdbfa-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
