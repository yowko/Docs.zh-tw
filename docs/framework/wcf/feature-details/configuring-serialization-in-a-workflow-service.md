---
title: 在工作流程服務中設定序列化
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 63a5860bd428fd4ce7fe01d7901427c85b2d5609
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154108"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="30e5b-102">在工作流程服務中設定序列化</span><span class="sxs-lookup"><span data-stu-id="30e5b-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="30e5b-103">工作流程服務是 Windows Communication Foundation (WCF) 服務，因此可以選擇使用<xref:System.Runtime.Serialization.DataContractSerializer>（預設值） 或<xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="30e5b-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="30e5b-104">撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。</span><span class="sxs-lookup"><span data-stu-id="30e5b-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="30e5b-105">建立 WCF workflow service 時未指定這些合約中的程式碼，但而不是在執行階段所產生合約推斷。</span><span class="sxs-lookup"><span data-stu-id="30e5b-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="30e5b-106">如需有關合約推斷的詳細資訊，請參閱[在工作流程中使用的合約](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="30e5b-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="30e5b-107">序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。</span><span class="sxs-lookup"><span data-stu-id="30e5b-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="30e5b-108">您可以在設計工具中設定此屬性，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="30e5b-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="30e5b-109">![設定序列化程式](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="30e5b-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="30e5b-110">您也可以在程式碼中設定序列化程式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30e5b-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 <span data-ttu-id="30e5b-111">此外，您也可以在工作流程服務上指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="30e5b-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="30e5b-112">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="30e5b-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="30e5b-113">您可以在設計工具或程式碼中指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="30e5b-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="30e5b-114">若要在設計工具中指定已知型別，請在 <xref:System.ServiceModel.Activities.Receive> 活動的 [屬性] 視窗中，按一下 KnownTypes 屬性旁的省略符號按鈕，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="30e5b-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="30e5b-115">![KnownTypes 屬性](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="30e5b-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="30e5b-116">這樣就會顯示 [型別集合編輯器]，可讓您搜尋和指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="30e5b-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="30e5b-117">![加入已知型別](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="30e5b-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="30e5b-118">按一下 **加入新的型別**連結，並用於下拉式清單選取或類型搜尋新增至已知型別集合。</span><span class="sxs-lookup"><span data-stu-id="30e5b-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="30e5b-119">若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="30e5b-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```csharp
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
