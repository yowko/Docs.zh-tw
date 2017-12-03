---
title: "HOW TO：鎖定企業的端點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c580316415a1186bbdee518e201fb4c88419a72
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-lock-down-endpoints-in-the-enterprise"></a><span data-ttu-id="570f9-102">HOW TO：鎖定企業的端點</span><span class="sxs-lookup"><span data-stu-id="570f9-102">How to: Lock Down Endpoints in the Enterprise</span></span>
<span data-ttu-id="570f9-103">大型企業通常需要在遵循企業安全性原則的環境中開發應用程式。</span><span class="sxs-lookup"><span data-stu-id="570f9-103">Large enterprises often require that applications are developed in compliance with enterprise security policies.</span></span> <span data-ttu-id="570f9-104">下列主題討論如何開發與安裝用戶端端點驗證器，以用於驗證所有安裝在電腦上的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="570f9-104">The following topic discusses how to develop and install a client endpoint validator that can be used to validate all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client applications installed on computers.</span></span>  
  
 <span data-ttu-id="570f9-105">驗證程式在此情況下，是用戶端驗證程式，因為此端點行為會加入至用戶端[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) machine.config 檔案中的區段。</span><span class="sxs-lookup"><span data-stu-id="570f9-105">In this case, the validator is a client validator because this endpoint behavior is added to the client [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section in the machine.config file.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="570f9-106"> 只會為用戶端應用程式載入通用端點行為，並且只會為服務應用程式載入通用服務行為。</span><span class="sxs-lookup"><span data-stu-id="570f9-106"> loads common endpoint behaviors only for client applications and loads common service behaviors only for service applications.</span></span> <span data-ttu-id="570f9-107">若要為服務應用程式安裝這個相同的驗證器，驗證器必須是服務行為。</span><span class="sxs-lookup"><span data-stu-id="570f9-107">To install this same validator for service applications, the validator must be a service behavior.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="570f9-108">[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) > 一節。</span><span class="sxs-lookup"><span data-stu-id="570f9-108"> the [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="570f9-109">服務或端點行為沒有標記為<xref:System.Security.AllowPartiallyTrustedCallersAttribute>屬性 (APTCA) 加入至[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)在部分信任中執行的應用程式時，不會執行組態檔區段當發生這種情況時，就會擲回環境，以及任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="570f9-109">Service or endpoint behaviors not marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute (APTCA) that are added to the [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section of a configuration file are not run when the application runs in a partial trust environment, and no exception is thrown when this occurs.</span></span> <span data-ttu-id="570f9-110">若要強制執行通用行為 (例如驗證器)，您必須執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="570f9-110">To enforce the running of common behaviors such as validators, you must either:</span></span>  
>   
>  <span data-ttu-id="570f9-111">-- 使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性標記您的通用行為，讓它可以在部署為部分信任應用程式時執行。</span><span class="sxs-lookup"><span data-stu-id="570f9-111">-- Mark your common behavior with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute so that it can run when deployed as a Partial Trust application.</span></span> <span data-ttu-id="570f9-112">請注意，您可以在電腦上設定登錄項目，以防止已標記 APTCA 的組件執行。</span><span class="sxs-lookup"><span data-stu-id="570f9-112">Note that a registry entry can be set on the computer to prevent APTCA-marked assemblies from running..</span></span>  
>   
>  <span data-ttu-id="570f9-113">-- 確定應用程式是否會部署為完全信任的應用程式，而使用者是否無法修改程式碼存取安全性設定以在部分信任環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="570f9-113">-- Ensure that if the application is deployed as a fully-trusted application that users cannot modify the code-access security settings to run the application in a Partial Trust environment.</span></span> <span data-ttu-id="570f9-114">如果可以執行這項操作，自訂驗證器就不會執行，也不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="570f9-114">If they can do so, the custom validator does not run and no exception is thrown.</span></span> <span data-ttu-id="570f9-115">若要確保這一種方法，請參閱`levelfinal`選項使用[程式碼存取安全性原則工具 (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222)。</span><span class="sxs-lookup"><span data-stu-id="570f9-115">For one way to ensure this, see the `levelfinal` option using [Code Access Security Policy Tool (Caspol.exe)](http://go.microsoft.com/fwlink/?LinkId=248222).</span></span>  
>   
>  <span data-ttu-id="570f9-116">如需詳細資訊，請參閱[部分信任最佳做法](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)和[支援的部署案例](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="570f9-116">For more information, see [Partial Trust Best Practices](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) and [Supported Deployment Scenarios](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).</span></span>  
  
### <a name="to-create-the-endpoint-validator"></a><span data-ttu-id="570f9-117">若要建立端點驗證器</span><span class="sxs-lookup"><span data-stu-id="570f9-117">To create the endpoint validator</span></span>  
  
1.  <span data-ttu-id="570f9-118">以 <xref:System.ServiceModel.Description.IEndpointBehavior> 方法中所需的驗證步驟建立 <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A>。</span><span class="sxs-lookup"><span data-stu-id="570f9-118">Create an <xref:System.ServiceModel.Description.IEndpointBehavior> with the desired validation steps in the <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A> method.</span></span> <span data-ttu-id="570f9-119">下列程式碼提供一個範例。</span><span class="sxs-lookup"><span data-stu-id="570f9-119">The following code provides an example.</span></span> <span data-ttu-id="570f9-120">(`InternetClientValidatorBehavior`取自[安全性驗證](../../../../docs/framework/wcf/samples/security-validation.md)範例。)</span><span class="sxs-lookup"><span data-stu-id="570f9-120">(The `InternetClientValidatorBehavior` is taken from the [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md) sample.)</span></span>  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  <span data-ttu-id="570f9-121">建立新的 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>，它會註冊步驟 1 中建立的端點驗證器。</span><span class="sxs-lookup"><span data-stu-id="570f9-121">Create new <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that registers the endpoint validator created in step 1.</span></span> <span data-ttu-id="570f9-122">下列程式碼範例會顯示這點。</span><span class="sxs-lookup"><span data-stu-id="570f9-122">The following code example shows this.</span></span> <span data-ttu-id="570f9-123">(此範例中的原始程式碼位於[安全性驗證](../../../../docs/framework/wcf/samples/security-validation.md)範例。)</span><span class="sxs-lookup"><span data-stu-id="570f9-123">(The original code for this example is in the [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md) sample.)</span></span>  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  <span data-ttu-id="570f9-124">請務必以強式名稱簽署編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="570f9-124">Make sure the compiled assembly is signed with a strong name.</span></span> <span data-ttu-id="570f9-125">如需詳細資訊，請參閱[強式名稱工具 (SN。EXE)](http://go.microsoft.com/fwlink/?LinkId=248217)與您的語言編譯器命令。</span><span class="sxs-lookup"><span data-stu-id="570f9-125">For details, see the [Strong Name Tool (SN.EXE)](http://go.microsoft.com/fwlink/?LinkId=248217) and the compiler commands for your language.</span></span>  
  
### <a name="to-install-the-validator-into-the-target-computer"></a><span data-ttu-id="570f9-126">若要將驗證器安裝至目標電腦</span><span class="sxs-lookup"><span data-stu-id="570f9-126">To install the validator into the target computer</span></span>  
  
1.  <span data-ttu-id="570f9-127">使用適當的機制安裝端點驗證器。</span><span class="sxs-lookup"><span data-stu-id="570f9-127">Install the endpoint validator using the appropriate mechanism.</span></span> <span data-ttu-id="570f9-128">在企業中，您可以使用群組原則和 Systems Management Server (SMS) 安裝端點驗證器。</span><span class="sxs-lookup"><span data-stu-id="570f9-128">In an enterprise, this can be using Group Policy and Systems Management Server (SMS).</span></span>  
  
2.  <span data-ttu-id="570f9-129">強式名稱組件安裝到全域組件快取使用[Gacutil.exe （全域組件快取工具）](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="570f9-129">Install the strongly-named assembly into the global assembly cache using the [Gacutil.exe (Global Assembly Cache Tool)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).</span></span>  
  
3.  <span data-ttu-id="570f9-130">使用 <xref:System.Configuration?displayProperty=nameWithType> 命名空間型別以：</span><span class="sxs-lookup"><span data-stu-id="570f9-130">Use the <xref:System.Configuration?displayProperty=nameWithType> namespace types to:</span></span>  
  
    1.  <span data-ttu-id="570f9-131">將延伸加入[ \<behaviorExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)區段使用完整限定類型名稱，並鎖定項目。</span><span class="sxs-lookup"><span data-stu-id="570f9-131">Add the extension to the [\<behaviorExtensions>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) section using a fully-qualified type name and lock the element.</span></span>  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  <span data-ttu-id="570f9-132">新增行為項目的`EndpointBehaviors`屬性[ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)區段，並鎖定項目。</span><span class="sxs-lookup"><span data-stu-id="570f9-132">Add the behavior element to the `EndpointBehaviors` property of the [\<commonBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) section and lock the element.</span></span> <span data-ttu-id="570f9-133">(若要在服務上安裝驗證器，驗證器必須是 <xref:System.ServiceModel.Description.IServiceBehavior> 並加入至 `ServiceBehaviors` 屬性)。下列程式碼範例將示範如何在步驟 a.</span><span class="sxs-lookup"><span data-stu-id="570f9-133">(To install the validator on the service, the validator must be an <xref:System.ServiceModel.Description.IServiceBehavior> and added to the `ServiceBehaviors` property.) The following code example shows the proper configuration after steps a.</span></span> <span data-ttu-id="570f9-134">和 b. 後進行適當的設定，唯一的例外是沒有強式名稱時。</span><span class="sxs-lookup"><span data-stu-id="570f9-134">and b., with the sole exception that there is no strong name.</span></span>  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  <span data-ttu-id="570f9-135">儲存 machine.config 檔。</span><span class="sxs-lookup"><span data-stu-id="570f9-135">Save the machine.config file.</span></span> <span data-ttu-id="570f9-136">下列程式碼範例執行步驟 3 中所有的工作，但將修改過的 machine.config 檔案複本儲存在本機上。</span><span class="sxs-lookup"><span data-stu-id="570f9-136">The following code example performs all the tasks in step 3 but saves a copy of the modified machine.config file locally.</span></span>  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="570f9-137">範例</span><span class="sxs-lookup"><span data-stu-id="570f9-137">Example</span></span>  
 <span data-ttu-id="570f9-138">下列程式碼範例示範如何將通用行為新增至 machine.config 檔案，並將複本儲存至磁碟上。</span><span class="sxs-lookup"><span data-stu-id="570f9-138">The following code example shows how to add a common behavior to the machine.config file and save a copy to the disk.</span></span> <span data-ttu-id="570f9-139">`InternetClientValidatorBehavior`取自[安全性驗證](../../../../docs/framework/wcf/samples/security-validation.md)範例。</span><span class="sxs-lookup"><span data-stu-id="570f9-139">The `InternetClientValidatorBehavior` is taken from the [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md) sample.</span></span>  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="570f9-140">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="570f9-140">.NET Framework Security</span></span>  
 <span data-ttu-id="570f9-141">您可能也要加密組態檔項目。</span><span class="sxs-lookup"><span data-stu-id="570f9-141">You may also want to encrypt the configuration file elements.</span></span> <span data-ttu-id="570f9-142">如需詳細資訊，請參閱「請參閱」一節。</span><span class="sxs-lookup"><span data-stu-id="570f9-142">For more information, see the See Also section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570f9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="570f9-143">See Also</span></span>  
 [<span data-ttu-id="570f9-144">使用 DPAPI 的加密組態檔項目</span><span class="sxs-lookup"><span data-stu-id="570f9-144">Encrypting configuration file elements using DPAPI</span></span>](http://go.microsoft.com/fwlink/?LinkId=94954)  
 [<span data-ttu-id="570f9-145">使用 RSA 加密組態檔項目</span><span class="sxs-lookup"><span data-stu-id="570f9-145">Encrypting configuration file elements using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=94955)
