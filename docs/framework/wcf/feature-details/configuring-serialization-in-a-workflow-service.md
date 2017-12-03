---
title: "在工作流程服務中設定序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78f963f61c7ec67d6104a90c047ce78b0470568a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="138ad-102">在工作流程服務中設定序列化</span><span class="sxs-lookup"><span data-stu-id="138ad-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="138ad-103">工作流程服務是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務，因此具有使用 <xref:System.Runtime.Serialization.DataContractSerializer> (預設值) 或 <xref:System.Xml.Serialization.XmlSerializer> 的選項。</span><span class="sxs-lookup"><span data-stu-id="138ad-103">Workflow services are [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="138ad-104">撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。</span><span class="sxs-lookup"><span data-stu-id="138ad-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="138ad-105">建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作流程服務時，您不會在程式碼中指定這些合約，而是由合約推斷在執行階段中產生合約。</span><span class="sxs-lookup"><span data-stu-id="138ad-105">When creating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="138ad-106">合約推斷，請參閱[工作流程中使用的合約](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="138ad-106"> contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="138ad-107">序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。</span><span class="sxs-lookup"><span data-stu-id="138ad-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="138ad-108">您可以在設計工具中設定此屬性，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="138ad-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="138ad-109">![設定序列化程式](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="138ad-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="138ad-110">您也可以在程式碼中設定序列化程式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="138ad-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 <span data-ttu-id="138ad-111">此外，您也可以在工作流程服務上指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="138ad-111">Known types can be specified on Workflow services as well.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="138ad-112">已知類型，請參閱[資料合約已知型別](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="138ad-112"> Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="138ad-113">您可以在設計工具或程式碼中指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="138ad-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="138ad-114">若要在設計工具中指定已知型別，請在 <xref:System.ServiceModel.Activities.Receive> 活動的 [屬性] 視窗中，按一下 KnownTypes 屬性旁的省略符號按鈕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="138ad-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="138ad-115">![KnownTypes 屬性](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="138ad-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="138ad-116">這樣就會顯示 [型別集合編輯器]，可讓您搜尋和指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="138ad-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="138ad-117">![加入已知型別](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="138ad-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="138ad-118">按一下**加入新的型別**連結，然後使用下拉式清單選取或搜尋為類型加入已知型別集合。</span><span class="sxs-lookup"><span data-stu-id="138ad-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="138ad-119">若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="138ad-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```  
  
 <span data-ttu-id="138ad-120">若要查看完整的程式碼範例示範如何設定工作流程服務的序列化看到[工作流程服務中的格式化訊息](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="138ad-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
