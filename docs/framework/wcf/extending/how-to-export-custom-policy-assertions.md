---
title: "HOW TO：匯出自訂原則判斷提示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 466aecb5102332d3e246fd340e43b482d2c17a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="02b06-102">HOW TO：匯出自訂原則判斷提示</span><span class="sxs-lookup"><span data-stu-id="02b06-102">How to: Export Custom Policy Assertions</span></span>
<span data-ttu-id="02b06-103">原則判斷提示描述服務端點的功能與需求。</span><span class="sxs-lookup"><span data-stu-id="02b06-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="02b06-104">服務應用程式可使用服務中繼資料中的自訂原則判斷提示，與用戶端應用程式進行端點、繫結或合約自訂資訊的通訊。</span><span class="sxs-lookup"><span data-stu-id="02b06-104">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="02b06-105">您可使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 附加於端點、作業或訊息物件 WSDL 繫結的原則運算式匯出判斷提示，根據您通訊的功能或要求而定。</span><span class="sxs-lookup"><span data-stu-id="02b06-105">You can use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="02b06-106">匯出自訂原則判斷提示的方法，是實作 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> 介面，然後直接將繫結項目插入服務端點的繫結或將繫結項目登錄於應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="02b06-106">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="02b06-107">您的原則匯出實作應將您的自訂原則判斷提示當成 <xref:System.Xml.XmlElement?displayProperty=nameWithType> 執行個體新增至位於傳入 <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> 方法的 <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> 上之合適 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>。</span><span class="sxs-lookup"><span data-stu-id="02b06-107">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="02b06-108">除此之外，您還必須檢查 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 類別的 <xref:System.ServiceModel.Description.WsdlExporter> 屬性 (Property)，並且根據指定的原則版本，以正確命名空間匯出巢狀原則運算式及原則架構屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="02b06-108">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="02b06-109">若要匯入自訂原則判斷提示，請參閱<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>和[How to： 匯入自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)。</span><span class="sxs-lookup"><span data-stu-id="02b06-109">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="02b06-110">若要匯出自訂原則判斷提示</span><span class="sxs-lookup"><span data-stu-id="02b06-110">To export custom policy assertions</span></span>  
  
1.  <span data-ttu-id="02b06-111">實作 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType><xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>上的  介面。</span><span class="sxs-lookup"><span data-stu-id="02b06-111">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="02b06-112">下列程式碼範例顯示繫結層級之自訂原則判斷提示的實作。</span><span class="sxs-lookup"><span data-stu-id="02b06-112">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  <span data-ttu-id="02b06-113">以程式設計的方式或使用應用程式組態檔將繫結項目插入端點繫結。</span><span class="sxs-lookup"><span data-stu-id="02b06-113">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="02b06-114">請參閱下列程序。</span><span class="sxs-lookup"><span data-stu-id="02b06-114">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="02b06-115">若要使用應用程式組態檔插入繫結項目</span><span class="sxs-lookup"><span data-stu-id="02b06-115">To insert a binding element using an application configuration file</span></span>  
  
1.  <span data-ttu-id="02b06-116">針對您的自訂原則判斷提示繫結項目實作 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="02b06-116">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2.  <span data-ttu-id="02b06-117">將繫結項目延伸加入至組態檔使用[ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)項目。</span><span class="sxs-lookup"><span data-stu-id="02b06-117">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3.  <span data-ttu-id="02b06-118">使用 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>建置自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="02b06-118">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="02b06-119">以程式設計的方式插入繫結項目</span><span class="sxs-lookup"><span data-stu-id="02b06-119">To insert a binding element programmatically</span></span>  
  
1.  <span data-ttu-id="02b06-120">建立新的 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> 並將它新增至 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="02b06-120">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="02b06-121">將步驟 1 中的自訂繫結加入。</span><span class="sxs-lookup"><span data-stu-id="02b06-121">Add the custom binding from step 1.</span></span> <span data-ttu-id="02b06-122">至新服務端點，並呼叫 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 方法，以將新服務端點加入至 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>。</span><span class="sxs-lookup"><span data-stu-id="02b06-122">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3.  <span data-ttu-id="02b06-123">開啟 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="02b06-123">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="02b06-124">下列程式碼範例顯示自訂繫結的建立，以及使用程式設計方式插入繫結項目。</span><span class="sxs-lookup"><span data-stu-id="02b06-124">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="02b06-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02b06-125">See Also</span></span>  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [<span data-ttu-id="02b06-126">如何： 匯入自訂原則判斷提示</span><span class="sxs-lookup"><span data-stu-id="02b06-126">How to: Import Custom Policy Assertions</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
