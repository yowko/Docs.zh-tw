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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aa50b8e9f29e5dd14f0ff18d253943a73ef3a0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a>在工作流程服務中設定序列化
工作流程服務是 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務，因此具有使用 <xref:System.Runtime.Serialization.DataContractSerializer> (預設值) 或 <xref:System.Xml.Serialization.XmlSerializer> 的選項。 撰寫非工作流程服務時，要使用的序列化程式型別會指定於服務或作業合約上。 建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工作流程服務時，您不會在程式碼中指定這些合約，而是由合約推斷在執行階段中產生合約。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]合約推斷，請參閱[工作流程中使用的合約](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)。  序列化程式是使用 <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> 屬性來指定。 您可以在設計工具中設定此屬性，如下圖所示。  
  
 ![設定序列化程式](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 您也可以在程式碼中設定序列化程式，如下列範例所示。  
  
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
  
 此外，您也可以在工作流程服務上指定已知型別。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]已知類型，請參閱[資料合約已知型別](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。 您可以在設計工具或程式碼中指定已知型別。 若要在設計工具中指定已知型別，請在 <xref:System.ServiceModel.Activities.Receive> 活動的 [屬性] 視窗中，按一下 KnownTypes 屬性旁的省略符號按鈕，如下圖所示。  
  
 ![KnownTypes 屬性](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 這樣就會顯示 [型別集合編輯器]，可讓您搜尋和指定已知型別。  
  
 ![加入已知型別](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
 按一下**加入新的型別**連結，然後使用下拉式清單選取或搜尋為類型加入已知型別集合。 若要在程式碼中指定已知型別，請使用 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 屬性，如下列範例所示。  
  
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
  
 若要查看完整的程式碼範例示範如何設定工作流程服務的序列化看到[工作流程服務中的格式化訊息](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md)。
