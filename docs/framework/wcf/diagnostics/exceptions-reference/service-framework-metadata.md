---
title: "服務架構中繼資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cab33ec4a3f3e42c4ec373073e171a7dcfeace2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="service-framework-metadata"></a>服務架構中繼資料
此主題會列出服務架構中繼資料產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|在錯誤的通道上呼叫非同步 End。|  
|AsyncEndCalledWithAnIAsyncResult|透過不同的 Begin 方法，使用 IAsyncResult 來呼叫非同步 End。|  
|AttemptedToGetContractTypeForButThatTypeIs1|嘗試取得指定之項目的合約類型。此類型不是 ServiceContract 而且並未繼承 ServiceContract。|  
|CannotHaveTwoOperationsWithTheSameName3|在同一份合約中，不可有兩個同名的作業。 指定之類型中的指定方法違反此規則。 藉由變更方法名稱或使用 OperationContractAttribute 的 Name 屬性，變更其中一項作業的名稱。|  
|CannotInheritTwoOperationsWithTheSameName3|無法繼承同名的兩個不同作業。 來自指定之合約的指定作業違反此規則。 藉由變更方法名稱或使用 OperationContractAttribute 的 Name 屬性，變更其中一項作業的名稱。|  
|CantCreateChannelWithManualAddressing|無法為需要要求/回覆的合約與需要手動定址的繫結建立通道，但是僅支援雙工通訊。|  
|DuplicateBehavior1|無法將值新增至集合。 集合已經包含具有相同指定之類型的項目。 此集合僅針對每個類型支援一個執行個體。|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|由於指定的基礎服務合約具有指定的回呼合約，指定的衍生服務合約必須同時將指定的類型或是衍生的類型指定為回呼合約。|  
|InvalidAsyncBeginMethodSignatureForMethod2|在指定的 ServiceContract 類型中，指定之方法的無效非同步 Begin 方法簽章。 您的 Begin 方法必須將 AsyncCallback 與某個物件當成最後兩個引數，並傳回 IAsyncResult。|  
|InvalidAsyncEndMethodSignatureForMethod2|在指定的 ServiceContract 類型中，指定之方法的無效非同步 End 方法簽章。 您的 End 方法必須將 IAsyncResult 當成最後一個引數。|  
|MessagePropertiesArraySize0|傳遞的陣列沒有足夠的空間來容納此集合所包含的全部屬性。|  
|OneWayAndFaultsIncompatible2|所指定類型中的指定方法會標示為 IsOneWay=true 並宣告一個或多個 FaultContractAttributes。 單向方法無法宣告 FaultContractAttributes。 請將 IsOneWay 變更為 false 或是移除 FaultContractAttributes。|  
|UnsupportedWSDLOnlyOneMessage|不支援的 Web 服務描述語言。 針對錯誤訊息僅支援一個訊息部分。 此錯誤訊息參考了一個以上的訊息部分。 如果您具有 Web 服務描述語言檔的編輯存取權限，則可以藉由移除額外的訊息部分，讓錯誤訊息僅參考一個部分來解決這個問題。|  
|UnsupportedWSDLTheFault|不支援的 Web 服務描述語言。 錯誤訊息部分必須參考一個項目。 此錯誤訊息並未參考項目。 如果您具有 Web 服務定義語言文件的編輯存取權限，則可以透過使用 'element' 屬性來參考結構描述項目以解決這個問題。|  
|WsdlImportErrorDependencyDetail|匯入其他指定值所依存的指定項目時發生錯誤。 同時指定了 Xpath。|  
|XsdMissingRequiredAttribute1|缺少指定的必要屬性。|
