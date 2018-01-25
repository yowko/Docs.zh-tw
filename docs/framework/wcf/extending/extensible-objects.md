---
title: "可延伸物件"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1bb341d9e164b1ce232f238f8ddf4a0cf807363
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="extensible-objects"></a>可延伸物件
可延伸物件模式是用於以新功能延伸現有的執行階段類別，或將新狀態新增至物件。 附加至其中一個可擴充物件的擴充功能會在處理程序中的各種不同階段啟用行為，以存取附加至它們可存取之一般可擴充物件的共用狀態與功能。  
  
## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > 模式  
 在可延伸物件模式中有三種介面：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。  
  
 <xref:System.ServiceModel.IExtensibleObject%601> 介面是由允許 <xref:System.ServiceModel.IExtension%601> 物件自訂其功能的類型所實作的。  
  
 可延伸物件允許 <xref:System.ServiceModel.IExtension%601> 物件的動態彙總。 <xref:System.ServiceModel.IExtension%601> 物件是使用下列介面描述特徵：  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 類型限制可保證只能定義做為 <xref:System.ServiceModel.IExtensibleObject%601> 之類別的延伸。 <xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 提供了彙總或分解的通知。  
  
 對於限制何時可新增及從擁有者中移除的實作是有效的。 例如，您可以不允許整個移除、不允許在擁有者或延伸處於特定狀態時新增或移除延伸、不允許同時新增多個擁有者，或只允許單一新增後接著單一移除。  
  
 <xref:System.ServiceModel.IExtension%601> 不代表與其他標準 Managed 介面的任何互動。 特別是，擁有者物件上的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法通常不會中斷連結它的延伸。  
  
 當擴充功能加入至集合，<xref:System.ServiceModel.IExtension%601.Attach%2A>進入集合之前呼叫。 從集合中，移除擴充功能時<xref:System.ServiceModel.IExtension%601.Detach%2A>移除之後呼叫。 這表示 （假設適當的同步處理） 擴充功能可以倚賴才發現它在集合中是之間<xref:System.ServiceModel.IExtension%601.Attach%2A>和<xref:System.ServiceModel.IExtension%601.Detach%2A>。  
  
 傳遞至 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 或 <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> 的物件不需要是 <xref:System.ServiceModel.IExtension%601> (例如，您可以傳遞任何物件)，但是傳回的延伸是 <xref:System.ServiceModel.IExtension%601>。  
  
 如果集合中的任何延伸模組不是<xref:System.ServiceModel.IExtension%601>，<xref:System.ServiceModel.IExtensionCollection%601.Find%2A>會傳回 null，和<xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A>會傳回空集合。 如果多個延伸模組實作<xref:System.ServiceModel.IExtension%601>，<xref:System.ServiceModel.IExtensionCollection%601.Find%2A>傳回其中一個。 從 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 傳回的值是快照。
  
 有兩個主要案例。 第一個案例是使用 <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> 屬性做為型別字典，將狀態插入物件，讓另一個元件可使用型別來查閱它。  
  
 第二個案例是使用 <xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 屬性，讓物件可參與自訂行為，例如註冊事件、監看狀態轉換等等。  
  
 <xref:System.ServiceModel.IExtensionCollection%601> 介面是 <xref:System.ServiceModel.IExtension%601> 物件的集合，這些物件允許依據 <xref:System.ServiceModel.IExtension%601> 的型別將其擷取。 <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> 會傳回最近所加入屬於該型別之 <xref:System.ServiceModel.IExtension%601> 的物件。  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Windows Communication Foundation 中的可延伸物件  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中有四種可延伸物件：  
  
-   <xref:System.ServiceModel.ServiceHostBase> – 這是服務之主機的基底類別。  這個類別的延伸可用於延伸 <xref:System.ServiceModel.ServiceHostBase> 本身的行為，或儲存各服務的狀態。  
  
-   <xref:System.ServiceModel.InstanceContext> – 這個類別會連接服務類型的執行個體與服務執行階段。  其中包含有關執行個體的資訊，以及包含 <xref:System.ServiceModel.InstanceContext> 之 <xref:System.ServiceModel.ServiceHostBase> 的參照。 這個類別的延伸可用於延伸 <xref:System.ServiceModel.InstanceContext> 的行為，或儲存各服務的狀態。  
  
-   <xref:System.ServiceModel.OperationContext> – 這個類別代表執行階段為各作業蒐集的作業資訊。  其中包括的資訊如傳入訊息標頭、傳入訊息屬性、傳入安全性身分識別和其他資訊。  這個類別的延伸可以延伸 <xref:System.ServiceModel.OperationContext> 的行為，或儲存各作業的狀態。  
  
-   <xref:System.ServiceModel.IContextChannel> – 這個介面允許檢查由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段所建置的通道和 Proxy 的各個狀態。  這個類別的延伸可以延伸 <xref:System.ServiceModel.IClientChannel> 的行為，或可用它來儲存各通道的狀態。  
  
-  
  
 下列程式碼範例將示範如何使用簡單的延伸來追蹤 <xref:System.ServiceModel.InstanceContext> 物件。  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.IExtensibleObject%601>  
 <xref:System.ServiceModel.IExtension%601>  
 <xref:System.ServiceModel.IExtensionCollection%601>
