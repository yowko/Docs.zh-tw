---
title: WCF 組態結構描述
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: baea1e49bce10054530afa5b6f282023d5ceb981
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755804"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="f7baf-102">WCF 組態結構描述</span><span class="sxs-lookup"><span data-stu-id="f7baf-102">WCF Configuration Schema</span></span>
<span data-ttu-id="f7baf-103">Windows Communication Foundation (WCF) 組態項目可讓您設定 WCF 服務和用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7baf-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="f7baf-104">您可使用[組態編輯器工具 (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) 來建立並修改用戶端與服務的組態檔。</span><span class="sxs-lookup"><span data-stu-id="f7baf-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="f7baf-105">由於組態檔採用 XML 格式，因此，如果要使用文字編輯器手動編輯這些檔案，則必須熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="f7baf-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="f7baf-106">否則，您可能會碰到 XML 項目標記或屬性找不到等問題，</span><span class="sxs-lookup"><span data-stu-id="f7baf-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="f7baf-107">因為 XML 項目標記與屬性有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f7baf-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="f7baf-108">WCF 組態系統根據<xref:System.Configuration>命名空間。</span><span class="sxs-lookup"><span data-stu-id="f7baf-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="f7baf-109">因此，您可以使用 <xref:System.Configuration> 命名空間提供的所有標準功能，例如組態鎖定、加密與合併，以提升應用程式及其組態的安全性。</span><span class="sxs-lookup"><span data-stu-id="f7baf-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="f7baf-110">如需這些概念的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="f7baf-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="f7baf-111">加密組態資訊</span><span class="sxs-lookup"><span data-stu-id="f7baf-111">Encrypting Configuration Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [<span data-ttu-id="f7baf-112">鎖定組態設定</span><span class="sxs-lookup"><span data-stu-id="f7baf-112">Locking Configuration Settings</span></span>](https://go.microsoft.com/fwlink/?LinkId=95338)  
  
 <span data-ttu-id="f7baf-113">本節說明每個組態項目的所有可能值，以及項目如何與其他 WCF 組態項目互動。</span><span class="sxs-lookup"><span data-stu-id="f7baf-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="f7baf-114">下圖說明 WCF 組態結構描述：</span><span class="sxs-lookup"><span data-stu-id="f7baf-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![此圖顯示 WCF 組態結構描述。](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
>  <span data-ttu-id="f7baf-116">您應該保護在您的應用程式組態檔 (app.config) 具有適當存取控制清單 (ACL) 以避免任何潛在的安全性威脅的 WCF 組態區段。</span><span class="sxs-lookup"><span data-stu-id="f7baf-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="f7baf-117">例如，您要確定只有適當人員才能存取或修改應用程式繫結上的安全性設定，或是服務組態檔的服務模型區段。</span><span class="sxs-lookup"><span data-stu-id="f7baf-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7baf-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="f7baf-118">In This Section</span></span>  
 [<span data-ttu-id="f7baf-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f7baf-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="f7baf-120">說明 `ServiceModel` 項目。</span><span class="sxs-lookup"><span data-stu-id="f7baf-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="f7baf-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f7baf-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="f7baf-122">設定 SMSvcHost.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="f7baf-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="f7baf-123">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f7baf-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="f7baf-124">使用 <xref:System.Runtime.Serialization.DataContractSerializer> 等序列化程式時，設定選項的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="f7baf-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7baf-125">相關章節</span><span class="sxs-lookup"><span data-stu-id="f7baf-125">Related Sections</span></span>  
 [<span data-ttu-id="f7baf-126">設定 Windows Communication Foundation 應用程式</span><span class="sxs-lookup"><span data-stu-id="f7baf-126">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="f7baf-127">描述如何設定 WCF 服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="f7baf-127">Describes how to configure WCF services and clients.</span></span>
