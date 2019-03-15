---
title: 在工作流程服務中設定序列化
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843925"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>在工作流程服務中設定序列化
工作流程服務是 Windows Communication Foundation (WCF) 服務，因此可以選擇使用<xref:System.Runtime.Serialization.DataContractSerializer>（預設值） 或<xref:System.Xml.Serialization.XmlSerializer>。 撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。 建立 WCF workflow service 時未指定這些合約中的程式碼，但而不是在執行階段所產生合約推斷。 如需有關合約推斷的詳細資訊，請參閱[在工作流程中使用的合約](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。  序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。 您可以在設計工具中設定此屬性，如下圖所示。  
  
 ![在 [屬性] 視窗中設定 SerializerOption; 屬性。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
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
  
  此外，您也可以在工作流程服務上指定已知型別。 如需已知類型的詳細資訊，請參閱[Data Contract Known Types](data-contract-known-types.md)。 您可以在設計工具或程式碼中指定已知型別。 若要指定已知型別設計工具中，按一下 [在 KnownTypes 屬性旁的省略符號按鈕**屬性] 視窗**如<xref:System.ServiceModel.Activities.Receive>活動，如下圖所示。   
  
 ![KnownTypes 屬性 對話方塊的螢幕擷取畫面。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 這會顯示型別集合編輯器，可讓您搜尋和指定已知型別。  
  
 ![型別集合編輯器的螢幕擷取畫面。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 按一下 **加入新的型別**連結，並用於下拉式清單選取或類型搜尋新增至已知型別集合。 若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。  
  
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
