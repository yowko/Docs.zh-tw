---
title: 在工作流程服務中設定序列化
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: d1cda33c8a469b4a54b6d282b99c07b23e91543e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284195"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>在工作流程服務中設定序列化

工作流程服務是 Windows Communication Foundation (WCF) 服務，因此可以選擇使用 <xref:System.Runtime.Serialization.DataContractSerializer> (預設的) 或 <xref:System.Xml.Serialization.XmlSerializer> 。 撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。 建立 WCF 工作流程服務時，您不會在程式碼中指定這些合約，而是由合約推斷在執行時間產生。 如需有關合約推斷的詳細資訊，請參閱  [在工作流程中使用合約](using-contracts-in-workflow.md)。  序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。 您可以在設計工具中設定此屬性，如下圖所示。  
  
 ![在 [屬性] 視窗中設定 SerializerOption 屬性。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 您也可以在程式碼中設定序列化程式，如下列範例所示。  
  
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
  
  此外，您也可以在工作流程服務上指定已知型別。 如需已知類型的詳細資訊，請參閱 [資料合約已知類型](data-contract-known-types.md)。 您可以在設計工具或程式碼中指定已知型別。 若要在設計工具中指定已知類型，請在活動的 [ **屬性] 視窗** 中，按一下 [KnownTypes] 屬性旁邊的省略號按鈕，如下 <xref:System.ServiceModel.Activities.Receive> 圖所示。
  
 ![[KnownTypes 屬性] 對話方塊的螢幕擷取畫面。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 這會顯示 [型別集合編輯器]，讓您能夠搜尋和指定已知型別。  
  
 ![[型別集合編輯器] 的螢幕擷取畫面。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 按一下 [ **加入新的型** 別] 連結，然後使用下拉式清單來選取或搜尋要加入至已知型別集合的型別。 若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。  
  
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
