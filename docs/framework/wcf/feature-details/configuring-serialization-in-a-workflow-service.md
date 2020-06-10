---
title: 在工作流程服務中設定序列化
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597536"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="2ee16-102">在工作流程服務中設定序列化</span><span class="sxs-lookup"><span data-stu-id="2ee16-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="2ee16-103">工作流程服務是 Windows Communication Foundation （WCF）服務，因此可以選擇使用 <xref:System.Runtime.Serialization.DataContractSerializer> （預設值）或 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="2ee16-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="2ee16-104">撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。</span><span class="sxs-lookup"><span data-stu-id="2ee16-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="2ee16-105">建立 WCF 工作流程服務時，您不會在程式碼中指定這些合約，而是由合約推斷在執行時間產生。</span><span class="sxs-lookup"><span data-stu-id="2ee16-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="2ee16-106">如需有關合約推斷的詳細資訊，請參閱[在工作流程中使用合約](using-contracts-in-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee16-106">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="2ee16-107">序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。</span><span class="sxs-lookup"><span data-stu-id="2ee16-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="2ee16-108">您可以在設計工具中設定此屬性，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2ee16-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![在 [屬性] 視窗中設定 SerializerOption 屬性。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="2ee16-110">您也可以在程式碼中設定序列化程式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2ee16-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="2ee16-111">此外，您也可以在工作流程服務上指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="2ee16-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="2ee16-112">如需已知類型的詳細資訊，請參閱[資料合約已知類型](data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee16-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="2ee16-113">您可以在設計工具或程式碼中指定已知型別。</span><span class="sxs-lookup"><span data-stu-id="2ee16-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="2ee16-114">若要在設計工具中指定已知類型，請在活動的 [**屬性] 視窗**中，按一下 [KnownTypes] 屬性旁邊的省略號按鈕，如下 <xref:System.ServiceModel.Activities.Receive> 圖所示。</span><span class="sxs-lookup"><span data-stu-id="2ee16-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![[KnownTypes 屬性] 對話方塊的螢幕擷取畫面。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="2ee16-116">這會顯示 [類型集合編輯器]，可讓您搜尋並指定已知類型。</span><span class="sxs-lookup"><span data-stu-id="2ee16-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![[類型集合編輯器] 的螢幕擷取畫面。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="2ee16-118">按一下 [**加入新的類型**] 連結，然後使用下拉式選來選取或搜尋要加入至已知類型集合的類型。</span><span class="sxs-lookup"><span data-stu-id="2ee16-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="2ee16-119">若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2ee16-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
