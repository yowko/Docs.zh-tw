---
title: 使用 ServiceHostFactory 擴充裝載
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: d2224ea683326679efdad368cf2ff7b2b95f4dba
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273122"
---
# <a name="extending-hosting-using-servicehostfactory"></a>使用 ServiceHostFactory 擴充裝載

<xref:System.ServiceModel.ServiceHost>在 Windows Communication Foundation 中裝載服務的標準 API (wcf) 是 wcf 架構中的擴充點。 使用者可以從 <xref:System.ServiceModel.ServiceHost> 衍生自己的主機類別，通常要覆寫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> 以使用 <xref:System.ServiceModel.Description.ServiceDescription> 以便在開啟服務之前以命令方式新增預設端點或修改行為。  
  
 在自我裝載的環境中，您不需要建立自訂 <xref:System.ServiceModel.ServiceHost>，因為您會撰寫可具現化主機的程式碼，然後在產生的主機上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open>。 您可以在這兩個步驟之間隨心所欲地執行所需的工作。 例如，您可以新增一個 <xref:System.ServiceModel.Description.IServiceBehavior>：  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 這個方法無法重複使用。 用來操控描述的程式碼會寫入主機程式 (在此情況中，為 Main() 函式) 的程式碼中，因此您很難在其他環境中重複使用此邏輯。 您也可以透過其他不需要命令式程式碼的方法，來新增 <xref:System.ServiceModel.Description.IServiceBehavior>。 您可以從 <xref:System.ServiceModel.ServiceBehaviorAttribute> 衍生屬性，並將其放在您的服務實作類型中，或是讓自訂行為變成可設定，並透過組態來加以動態撰寫。  
  
 但是，您也可以稍微修改一下範例，來解決這個問題。 其中一個方法，就是將可新增 ServiceBehavior 的程式碼從 `Main()` 移出，並移入 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之自訂衍生物的 <xref:System.ServiceModel.ServiceHost> 方法：  
  
```csharp
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 接著，在 `Main()` 中使用：  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 現在您已經將自訂邏輯封裝成完全的抽象概念，可輕易地重複用在許多不同的主機可執行檔上。  
  
 現在您可能還無法立即瞭解如何從網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 的內部使用這個自訂 <xref:System.ServiceModel.ServiceHost>。 這些環境與自我裝載環境不同，因為裝載環境是指代表應用程式具現化 <xref:System.ServiceModel.ServiceHost> 的環境。 IIS 和 WAS 裝載基礎結構對於您的自訂 <xref:System.ServiceModel.ServiceHost> 衍生物一無所知。  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> 便是用來解決從 IIS 或 WAS 內部存取自訂 <xref:System.ServiceModel.ServiceHost> 的問題。 因為從 <xref:System.ServiceModel.ServiceHost> 衍生的自訂主機是動態設定而且可能是各種型別，裝載環境不可能直接加以具現化。 相反地，WCF 會使用原廠模式來提供裝載環境與服務之實體類型之間的間接取值層。 除非您明確告知，否則它會使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 實作，以傳回 <xref:System.ServiceModel.ServiceHost> 執行個體。 但是，您也可以在指示詞中指定 factory 實值的 CLR 型別名稱，來提供您自己的 factory，以傳回衍生的主機 @ServiceHost 。  
  
 這麼做的用意在於，對於基本案例來說，實作自己的處理站應該會相當簡單。 例如，下列為自訂 <xref:System.ServiceModel.Activation.ServiceHostFactory> (可傳回衍生的 <xref:System.ServiceModel.ServiceHost>)：  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 若要使用此處理站來取代預設 factory，請在指示詞中提供型別名稱，如下所示 @ServiceHost ：  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 儘管技術上並未限制您可以對 <xref:System.ServiceModel.ServiceHost> (從 <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A> 傳回) 執行的事項，我們建議您盡可能讓處理站的實作保持簡潔。 如果您有許多自訂邏輯，最好是將該邏輯放在主機內，而不是在原廠內，以便可以重複使用。  
  
 對於裝載的應用程式開發介面，還有一個值得一提的層級。 WCF 也有 <xref:System.ServiceModel.ServiceHostBase> 和 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> <xref:System.ServiceModel.ServiceHost> 分別衍生的和 <xref:System.ServiceModel.Activation.ServiceHostFactory> 。 之所以提供這些項目是因為在某些比較進階的情節中，您必須使用自己的自訂建立項目來交換大部分的中繼資料系統。
