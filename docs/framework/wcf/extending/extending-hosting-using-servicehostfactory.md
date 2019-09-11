---
title: 使用 ServiceHostFactory 擴充裝載
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: de6a590b94285872dd77006eda7f86d5d629be9d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849910"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="0c716-102">使用 ServiceHostFactory 擴充裝載</span><span class="sxs-lookup"><span data-stu-id="0c716-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="0c716-103">在 Windows Communication Foundation <xref:System.ServiceModel.ServiceHost> （wcf）中裝載服務的標準 API 是 WCF 架構中的擴充點。</span><span class="sxs-lookup"><span data-stu-id="0c716-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="0c716-104">使用者可以從 <xref:System.ServiceModel.ServiceHost> 衍生自己的主機類別，通常要覆寫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> 以使用 <xref:System.ServiceModel.Description.ServiceDescription> 以便在開啟服務之前以命令方式新增預設端點或修改行為。</span><span class="sxs-lookup"><span data-stu-id="0c716-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="0c716-105">在自我裝載的環境中，您不需要建立自訂 <xref:System.ServiceModel.ServiceHost>，因為您會撰寫可具現化主機的程式碼，然後在產生的主機上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open>。</span><span class="sxs-lookup"><span data-stu-id="0c716-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="0c716-106">您可以在這兩個步驟之間隨心所欲地執行所需的工作。</span><span class="sxs-lookup"><span data-stu-id="0c716-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="0c716-107">例如，您可以新增一個 <xref:System.ServiceModel.Description.IServiceBehavior>：</span><span class="sxs-lookup"><span data-stu-id="0c716-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="0c716-108">這個方法無法重複使用。</span><span class="sxs-lookup"><span data-stu-id="0c716-108">This approach is not reusable.</span></span> <span data-ttu-id="0c716-109">用來操控描述的程式碼會寫入主機程式 (在此情況中，為 Main() 函式) 的程式碼中，因此您很難在其他環境中重複使用此邏輯。</span><span class="sxs-lookup"><span data-stu-id="0c716-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="0c716-110">您也可以透過其他不需要命令式程式碼的方法，來新增 <xref:System.ServiceModel.Description.IServiceBehavior>。</span><span class="sxs-lookup"><span data-stu-id="0c716-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="0c716-111">您可以從 <xref:System.ServiceModel.ServiceBehaviorAttribute> 衍生屬性，並將其放在您的服務實作類型中，或是讓自訂行為變成可設定，並透過組態來加以動態撰寫。</span><span class="sxs-lookup"><span data-stu-id="0c716-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="0c716-112">但是，您也可以稍微修改一下範例，來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="0c716-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="0c716-113">其中一個方法，就是將可新增 ServiceBehavior 的程式碼從 `Main()` 移出，並移入 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之自訂衍生物的 <xref:System.ServiceModel.ServiceHost> 方法：</span><span class="sxs-lookup"><span data-stu-id="0c716-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
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
  
 <span data-ttu-id="0c716-114">接著，在 `Main()` 中使用：</span><span class="sxs-lookup"><span data-stu-id="0c716-114">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="0c716-115">現在您已經將自訂邏輯封裝成完全的抽象概念，可輕易地重複用在許多不同的主機可執行檔上。</span><span class="sxs-lookup"><span data-stu-id="0c716-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="0c716-116">現在您可能還無法立即瞭解如何從網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 的內部使用這個自訂 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="0c716-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="0c716-117">這些環境與自我裝載環境不同，因為裝載環境是指代表應用程式具現化 <xref:System.ServiceModel.ServiceHost> 的環境。</span><span class="sxs-lookup"><span data-stu-id="0c716-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="0c716-118">IIS 和 WAS 裝載基礎結構對於您的自訂 <xref:System.ServiceModel.ServiceHost> 衍生物一無所知。</span><span class="sxs-lookup"><span data-stu-id="0c716-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="0c716-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> 便是用來解決從 IIS 或 WAS 內部存取自訂 <xref:System.ServiceModel.ServiceHost> 的問題。</span><span class="sxs-lookup"><span data-stu-id="0c716-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="0c716-120">因為從 <xref:System.ServiceModel.ServiceHost> 衍生的自訂主機是動態設定而且可能是各種型別，裝載環境不可能直接加以具現化。</span><span class="sxs-lookup"><span data-stu-id="0c716-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="0c716-121">相反地，WCF 會使用 factory 模式來提供主控環境與服務的具象型別之間的間接取值層。</span><span class="sxs-lookup"><span data-stu-id="0c716-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="0c716-122">除非您明確告知，否則它會使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 實作，以傳回 <xref:System.ServiceModel.ServiceHost> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0c716-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="0c716-123">但是，您也可以透過在指示詞中@ServiceHost指定 factory 的 CLR 型別名稱，來提供您自己的 factory，以傳回您的衍生主機。</span><span class="sxs-lookup"><span data-stu-id="0c716-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="0c716-124">這麼做的用意在於，對於基本案例來說，實作自己的處理站應該會相當簡單。</span><span class="sxs-lookup"><span data-stu-id="0c716-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="0c716-125">例如，下列為自訂 <xref:System.ServiceModel.Activation.ServiceHostFactory> (可傳回衍生的 <xref:System.ServiceModel.ServiceHost>)：</span><span class="sxs-lookup"><span data-stu-id="0c716-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="0c716-126">若要使用這個處理站，而不是預設的 factory，請在@ServiceHost指示詞中提供型別名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c716-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="0c716-127">儘管技術上並未限制您可以對 <xref:System.ServiceModel.ServiceHost> (從 <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A> 傳回) 執行的事項，我們建議您盡可能讓處理站的實作保持簡潔。</span><span class="sxs-lookup"><span data-stu-id="0c716-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="0c716-128">如果您有許多自訂邏輯，最好將該邏輯放在您的主機中，而不是在原廠內部，以便可重複使用。</span><span class="sxs-lookup"><span data-stu-id="0c716-128">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="0c716-129">對於裝載的應用程式開發介面，還有一個值得一提的層級。</span><span class="sxs-lookup"><span data-stu-id="0c716-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="0c716-130">WCF 也具有<xref:System.ServiceModel.ServiceHostBase>和<xref:System.ServiceModel.Activation.ServiceHostFactoryBase> <xref:System.ServiceModel.ServiceHost> ，<xref:System.ServiceModel.Activation.ServiceHostFactory>分別衍生自和。</span><span class="sxs-lookup"><span data-stu-id="0c716-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="0c716-131">之所以提供這些項目是因為在某些比較進階的情節中，您必須使用自己的自訂建立項目來交換大部分的中繼資料系統。</span><span class="sxs-lookup"><span data-stu-id="0c716-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
