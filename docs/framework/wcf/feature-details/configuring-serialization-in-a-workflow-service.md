---
title: 在工作流程服務中設定序列化
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185339"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>在工作流程服務中設定序列化
工作流服務是 Windows 通信基礎 （WCF） 服務，因此可以選擇使用<xref:System.Runtime.Serialization.DataContractSerializer>（預設） 或<xref:System.Xml.Serialization.XmlSerializer>。 撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。 創建 WCF 工作流服務時，您不會在代碼中指定這些協定，而是在運行時通過協定推斷生成這些協定。 有關協定推理的詳細資訊，請參閱[在工作流中使用協定](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。  序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。 您可以在設計工具中設定此屬性，如下圖所示。  
  
 ![在屬性視窗中設置序列化程式選項屬性。](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
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
  
  此外，您也可以在工作流程服務上指定已知型別。 有關已知類型的詳細資訊，請參閱[資料協定已知類型](data-contract-known-types.md)。 您可以在設計工具或程式碼中指定已知型別。 要在設計器中指定已知類型，請按一下 **"屬性"視窗中**"已知類型"屬性旁邊的省略號按鈕，瞭解<xref:System.ServiceModel.Activities.Receive>活動，如下圖所示。
  
 !["已知類型"屬性對話方塊的螢幕截圖。](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 這將顯示允許您搜索和指定已知類型的類型集合編輯器。  
  
 ![類型集合編輯器的螢幕截圖。](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 按一下"**添加新類型**"連結，然後使用下拉清單選擇或搜索要添加到已知類型集合的類型。 若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。  
  
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
