---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed64a90131fcd8f2d9f2120c03db4a21d8dc6efe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="2a1c9-101">將用來產生服務主機的處理站，與要裝載的服務和存取或編譯 .svc 檔案中提供的程式碼所需的其他程式設計方面加以關聯。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1c9-102">語法</span><span class="sxs-lookup"><span data-stu-id="2a1c9-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="2a1c9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2a1c9-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="2a1c9-104">服務</span><span class="sxs-lookup"><span data-stu-id="2a1c9-104">Service</span></span>  
 <span data-ttu-id="2a1c9-105">所裝載之服務的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="2a1c9-106">這應該是實作一個以上的服務合約之型別的限定名稱。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="2a1c9-107">Factory</span><span class="sxs-lookup"><span data-stu-id="2a1c9-107">Factory</span></span>  
 <span data-ttu-id="2a1c9-108">用來具現化服務主機的服務主機處理站之 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="2a1c9-109">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-109">This attribute is optional.</span></span> <span data-ttu-id="2a1c9-110">如果沒有指定，則使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，它會傳回 <xref:System.ServiceModel.ServiceHost> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="2a1c9-111">偵錯</span><span class="sxs-lookup"><span data-stu-id="2a1c9-111">Debug</span></span>  
 <span data-ttu-id="2a1c9-112">表示 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務是否應該使用偵錯符號進行編譯。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-112">Indicates whether the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service should be compiled with debug symbols.</span></span> <span data-ttu-id="2a1c9-113">如果 `true` 服務應以偵錯符號編譯，則為 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-113">`true` if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="2a1c9-114">語言</span><span class="sxs-lookup"><span data-stu-id="2a1c9-114">Language</span></span>  
 <span data-ttu-id="2a1c9-115">指定編譯檔案內 (.svc) 所有內嵌程式碼時使用的語言。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="2a1c9-116">這些值可以表示任何 .NET 支援的語言，包括 C#、VB 和 JS (分別指 C#、Visual Basic .NET 和 JScript .NET)。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="2a1c9-117">這是一個選擇性的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="2a1c9-118">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="2a1c9-118">CodeBehind</span></span>  
 <span data-ttu-id="2a1c9-119">當實作 XML Web Service 的類別不是存放在相同的檔案中，且尚未編譯為組件並置於 \Bin 目錄內的時候，請指定實作 XML Web Service 的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a1c9-120">備註</span><span class="sxs-lookup"><span data-stu-id="2a1c9-120">Remarks</span></span>  
 <span data-ttu-id="2a1c9-121">用來裝載服務的 <xref:System.ServiceModel.ServiceHost> 是 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 程式設計模型中的擴充點。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] programming model.</span></span> <span data-ttu-id="2a1c9-122">因為 <xref:System.ServiceModel.ServiceHost> 是潛在的多型型別，而裝載環境不應直接具現化多型型別，所以使用處理站模式加以具現化。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="2a1c9-123">預設實作會使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2a1c9-124">您可以指定在您處理站實作的 CLR 型別名稱，以提供自己的處理站 （一個會傳回衍生的主機），但[ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="2a1c9-125">若要使用您自己的自訂服務裝載 factory 而非預設的 factory，只提供中的類型名稱[ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a1c9-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="2a1c9-126">盡可能保持處理站實作的簡便。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="2a1c9-127">假設您有許多自訂邏輯，那麼若您將邏輯放在主機而非處理站內，則這些程式碼就更能重複使用。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="2a1c9-128">例如，若要啟用的啟用 AJAX 的端點`MyService`，指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>值的`Factory`屬性，而不使用預設<xref:System.ServiceModel.Activation.ServiceHostFactory>，請在[ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)為指示詞下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2a1c9-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a1c9-129">範例</span><span class="sxs-lookup"><span data-stu-id="2a1c9-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a1c9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a1c9-130">See Also</span></span>  
 [<span data-ttu-id="2a1c9-131">自訂服務主機</span><span class="sxs-lookup"><span data-stu-id="2a1c9-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)
