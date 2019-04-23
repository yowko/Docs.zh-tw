---
title: .NET Framework 系統管理員部署手冊
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41cdc3db069ecf7ea854b76ac45d4b268a357459
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309507"
---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="d28ce-102">.NET Framework 系統管理員部署手冊</span><span class="sxs-lookup"><span data-stu-id="d28ce-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="d28ce-103">這篇逐步解說文章將描述系統管理員如何使用 Microsoft System Center Configuration Manager，在整個網路上部署 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 及其系統相依性。</span><span class="sxs-lookup"><span data-stu-id="d28ce-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="d28ce-104">本文章假設所有目標用戶端電腦都符合 .NET Framework 的最低需求。</span><span class="sxs-lookup"><span data-stu-id="d28ce-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="d28ce-105">如需安裝 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的軟體和硬體需求清單，請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d28ce-106">本文中提到的軟體包括 (但不限於) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、System Center Configuration Manager 和 Active Directory，這些軟體皆受授權條款和條件之限制。</span><span class="sxs-lookup"><span data-stu-id="d28ce-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="d28ce-107">這些指示假定軟體之適當使用人均已檢視並接受該等授權條款和條件。</span><span class="sxs-lookup"><span data-stu-id="d28ce-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="d28ce-108">這些指示不可撤回任何該等授權合約之規定條件。</span><span class="sxs-lookup"><span data-stu-id="d28ce-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="d28ce-109">如需 .NET Framework 支援的資訊，請參閱 Microsoft 技術支援網站上的 [Microsoft .NET Framework 支援週期原則](https://go.microsoft.com/fwlink/?LinkId=196607)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](https://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="d28ce-110">此主題包括下列章節：</span><span class="sxs-lookup"><span data-stu-id="d28ce-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="d28ce-111">部署程序</span><span class="sxs-lookup"><span data-stu-id="d28ce-111">The deployment process</span></span>](#the_deployment_process)  
 [<span data-ttu-id="d28ce-112">部署 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d28ce-112">Deploying the .NET Framework</span></span>](#deploying_in_a_test_environment)  
 [<span data-ttu-id="d28ce-113">建立集合</span><span class="sxs-lookup"><span data-stu-id="d28ce-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="d28ce-114">建立套件和程式</span><span class="sxs-lookup"><span data-stu-id="d28ce-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="d28ce-115">選取發佈點</span><span class="sxs-lookup"><span data-stu-id="d28ce-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="d28ce-116">部署套件</span><span class="sxs-lookup"><span data-stu-id="d28ce-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="d28ce-117">資源</span><span class="sxs-lookup"><span data-stu-id="d28ce-117">Resources</span></span>](#resources)  
[<span data-ttu-id="d28ce-118">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d28ce-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="d28ce-119">部署程序</span><span class="sxs-lookup"><span data-stu-id="d28ce-119">The deployment process</span></span>  
 <span data-ttu-id="d28ce-120">一旦您備妥提供支援的基礎結構之後，便可以用 System Center 2012 Configuration Manager 將 .NET Framework 可轉散發套件部署到網路上的電腦。</span><span class="sxs-lookup"><span data-stu-id="d28ce-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="d28ce-121">建置基礎結構包括建立和定義五個主要部分：集合、軟體套件和程式、發佈點以及部署。</span><span class="sxs-lookup"><span data-stu-id="d28ce-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="d28ce-122">**集合**：集合是指例如使用者、使用者群組或電腦等 Configuration Manager 資源的群組，也就是 .NET Framework 部署的目標。</span><span class="sxs-lookup"><span data-stu-id="d28ce-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="d28ce-123">如需詳細資訊，請參閱 Configuration Manager 文件庫中的 [System Center Configuration Manager 的集合簡介](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-123">For more information, see [Introduction to collections in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="d28ce-124">**套件和程式**：通常代表要安裝到用戶端電腦上的軟體應用程式，不過也可能包含個別檔案、更新，甚至個別命令。</span><span class="sxs-lookup"><span data-stu-id="d28ce-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="d28ce-125">如需詳細資訊，請參閱 Configuration Manager 文件庫中的 [System Center Configuration Manager 中的套件與程式](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-125">For more information, see [Packages and programs in System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="d28ce-126">**發佈點**：是指 Configuration Manager 網站系統角色，負責存放軟體在用戶端電腦上執行所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="d28ce-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="d28ce-127">當 Configuration Manager 用戶端接收並處理軟體部署時，就會連絡發佈點，以便下載軟體相關內容並啟動安裝程序。</span><span class="sxs-lookup"><span data-stu-id="d28ce-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="d28ce-128">如需詳細資訊，請參閱 Configuration Manager 文件庫中的 [Configuration Manager 中的內容管理基本概念](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-128">For more information, see [Fundamental concepts for content management in Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="d28ce-129">**部署**：負責指示所指定目標集合的適當成員安裝軟體套件。</span><span class="sxs-lookup"><span data-stu-id="d28ce-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="d28ce-130">本主題中的程序包含建立和部署套件與程式的一般設定，不過可能無法涵蓋所有可能的設定。</span><span class="sxs-lookup"><span data-stu-id="d28ce-130">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="d28ce-131">如需其他 Configuration Manager 部署選項，請參閱 [Configuration Manager 文件庫](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-131">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="d28ce-132">部署 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d28ce-132">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="d28ce-133">您可以使用 System Center 2012 Configuration Manager 部署 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的無訊息安裝，也就是說使用者不會與安裝程序互動。</span><span class="sxs-lookup"><span data-stu-id="d28ce-133">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="d28ce-134">請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d28ce-134">Follow these steps:</span></span>  
  
1. <span data-ttu-id="d28ce-135">[建立集合](#creating_a_collection)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-135">[Create a collection](#creating_a_collection).</span></span>  
  
2. <span data-ttu-id="d28ce-136">[建立 .NET Framework 可轉散發套件的套件和程式](#creating_a_package)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-136">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3. <span data-ttu-id="d28ce-137">[選取發佈點](#select_dist_point)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-137">[Select a distribution point](#select_dist_point).</span></span>  
  
4. <span data-ttu-id="d28ce-138">[部署套件](#deploying_package)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-138">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="d28ce-139">建立集合</span><span class="sxs-lookup"><span data-stu-id="d28ce-139">Create a collection</span></span>  
 <span data-ttu-id="d28ce-140">在這個步驟中，您將選取部署套件和程式的目標電腦，並將它們組成裝置集合。</span><span class="sxs-lookup"><span data-stu-id="d28ce-140">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="d28ce-141">若要在 Configuration Manager 中建立集合，您可以使用直接成員資格規則 (也就是手動指定集合成員) 或查詢規則 (也就是 Configuration Manager 根據您指定的準則決定集合成員)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-141">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="d28ce-142">如需包括查詢和直接規則的成員資格規則詳細資訊，請參閱 Configuration Manager 文件庫中的 [System Center Configuration Manager 的集合簡介](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-142">For more information about membership rules, including queries and direct rules, see [Introduction to collections in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="d28ce-143">若要建立集合：</span><span class="sxs-lookup"><span data-stu-id="d28ce-143">To create a collection:</span></span>  
  
1. <span data-ttu-id="d28ce-144">在 Configuration Manager 主控台中，選擇 [資產與相容性]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-144">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2. <span data-ttu-id="d28ce-145">在 [資產與相容性] 工作區中，選擇 [裝置集合]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-145">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3. <span data-ttu-id="d28ce-146">在 [首頁] 索引標籤的 [建立] 群組中，選擇 [建立裝置集合]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-146">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4. <span data-ttu-id="d28ce-147">在 [建立裝置集合精靈] 的 [一般] 頁面上，輸入集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="d28ce-147">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5. <span data-ttu-id="d28ce-148">選擇 [瀏覽] 以指定限制集合。</span><span class="sxs-lookup"><span data-stu-id="d28ce-148">Choose **Browse** to specify a limiting collection.</span></span>  
  
6. <span data-ttu-id="d28ce-149">在 [成員資格規則] 頁面上，選擇 [新增規則]，然後選擇 [直接規則] 開啟 [建立直接成員資格規則精靈]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-149">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="d28ce-150">選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-150">Choose **Next**.</span></span>  
  
7. <span data-ttu-id="d28ce-151">在 [搜尋資源] 頁面的 [資源類別] 清單中，選擇 [系統資源]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-151">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="d28ce-152">在 [屬性名稱] 清單中，選擇 [名稱]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-152">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="d28ce-153">在 [值] 欄位中輸入 `%`，然後選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-153">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8. <span data-ttu-id="d28ce-154">在 [選取資源] 頁面中，選取要在其中部署 .NET Framework 之每一部電腦的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d28ce-154">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="d28ce-155">選擇 [下一步]，然後完成精靈。</span><span class="sxs-lookup"><span data-stu-id="d28ce-155">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="d28ce-156">在 [建立裝置集合精靈] 的 [成員資格規則] 頁面上，選擇 [下一步]，然後完成精靈。</span><span class="sxs-lookup"><span data-stu-id="d28ce-156">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="d28ce-157">建立 .NET Framework 可轉散發套件的套件和程式</span><span class="sxs-lookup"><span data-stu-id="d28ce-157">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="d28ce-158">下列步驟會手動建立 .NET Framework 可轉散發套件的封裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-158">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="d28ce-159">套件包含指定的 .NET Framework 安裝參數，以及要從中將套件散發至目標電腦的來源位置。</span><span class="sxs-lookup"><span data-stu-id="d28ce-159">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="d28ce-160">若要建立封裝：</span><span class="sxs-lookup"><span data-stu-id="d28ce-160">To create a package:</span></span>  
  
1. <span data-ttu-id="d28ce-161">在 Configuration Manager 主控台中，選擇 [軟體程式庫]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-161">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2. <span data-ttu-id="d28ce-162">在 [軟體程式庫] 工作區中展開 [應用程式管理]，然後選擇 [套件]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-162">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3. <span data-ttu-id="d28ce-163">在 [首頁] 索引標籤的 [建立] 群組中，選擇 [建立套件]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-163">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4. <span data-ttu-id="d28ce-164">在 [建立套件和程式精靈] 的 [套件] 頁面上，輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d28ce-164">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="d28ce-165">名稱：</span><span class="sxs-lookup"><span data-stu-id="d28ce-165">Name:</span></span> `.NET Framework 4.5`  
  
    -   <span data-ttu-id="d28ce-166">製造商：</span><span class="sxs-lookup"><span data-stu-id="d28ce-166">Manufacturer:</span></span> `Microsoft`  
  
    -   <span data-ttu-id="d28ce-167">語言。</span><span class="sxs-lookup"><span data-stu-id="d28ce-167">Language.</span></span> `English (US)`  
  
5. <span data-ttu-id="d28ce-168">選擇 [此套件包含來源檔案]，然後選擇 [瀏覽] 以選取包含 .NET Framework 安裝檔案的本機或網路資料夾。</span><span class="sxs-lookup"><span data-stu-id="d28ce-168">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="d28ce-169">選取資料夾後，選擇 [確定]，然後選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-169">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6. <span data-ttu-id="d28ce-170">在精靈的 [程式類型] 頁面上，選擇 [標準程式]，然後選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-170">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7. <span data-ttu-id="d28ce-171">在 [建立套件和程式精靈] 的 [程式] 頁面上，輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d28ce-171">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  **<span data-ttu-id="d28ce-172">名稱：</span><span class="sxs-lookup"><span data-stu-id="d28ce-172">Name:</span></span>** `.NET Framework 4.5`  
  
    2.  <span data-ttu-id="d28ce-173">**命令列︰** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (這些步驟後的資料表中會說明命令列選項)</span><span class="sxs-lookup"><span data-stu-id="d28ce-173">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="d28ce-174">**執行：** 選擇 [隱藏]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-174">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="d28ce-175">**程式可以執行：** 選擇這個選項會指定無論使用者是否登入，程式都可以執行。</span><span class="sxs-lookup"><span data-stu-id="d28ce-175">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8. <span data-ttu-id="d28ce-176">在 [需求] 頁面上，選擇 [下一步] 接受預設值，然後完成精靈。</span><span class="sxs-lookup"><span data-stu-id="d28ce-176">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="d28ce-177">下表描述在步驟 7 中指定的命令列選項。</span><span class="sxs-lookup"><span data-stu-id="d28ce-177">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="d28ce-178">選項</span><span class="sxs-lookup"><span data-stu-id="d28ce-178">Option</span></span>|<span data-ttu-id="d28ce-179">說明</span><span class="sxs-lookup"><span data-stu-id="d28ce-179">Description</span></span>|  
|------------|-----------------|  
|**<span data-ttu-id="d28ce-180">/q</span><span class="sxs-lookup"><span data-stu-id="d28ce-180">/q</span></span>**|<span data-ttu-id="d28ce-181">設定無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="d28ce-181">Sets quiet mode.</span></span> <span data-ttu-id="d28ce-182">不需要使用者輸入，也不會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="d28ce-182">No user input is required, and no output is shown.</span></span>|  
|**<span data-ttu-id="d28ce-183">/norestart</span><span class="sxs-lookup"><span data-stu-id="d28ce-183">/norestart</span></span>**|<span data-ttu-id="d28ce-184">避免安裝程式自動重新開機。</span><span class="sxs-lookup"><span data-stu-id="d28ce-184">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="d28ce-185">如果您使用這個選項，Configuration Manager 就必須處理電腦重新啟動。</span><span class="sxs-lookup"><span data-stu-id="d28ce-185">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="d28ce-186">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="d28ce-186">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="d28ce-187">指定執行鏈結之封裝的名稱。</span><span class="sxs-lookup"><span data-stu-id="d28ce-187">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="d28ce-188">已註冊 [Microsoft 客戶經驗改進計劃](https://go.microsoft.com/fwlink/p/?LinkId=248244)的人將會收到這項資訊與其他安裝工作階段資訊的報告。</span><span class="sxs-lookup"><span data-stu-id="d28ce-188">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="d28ce-189">如果套件名稱包含空格，分隔符號請使用雙引號，例如：**/chainingpackage "Chaining Product"**。</span><span class="sxs-lookup"><span data-stu-id="d28ce-189">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="d28ce-190">這些步驟會建立名為 .NET Framework 4.5 的套件。</span><span class="sxs-lookup"><span data-stu-id="d28ce-190">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="d28ce-191">程式會部署 .NET Framework 4.5 的無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-191">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="d28ce-192">在無訊息安裝中，使用者不會與安裝程序互動，而鏈結應用程式必須擷取傳回碼並處理重新開機，請參閱[取得安裝套件的進度資訊](https://go.microsoft.com/fwlink/?LinkId=179606)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-192">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](https://go.microsoft.com/fwlink/?LinkId=179606).</span></span>  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="d28ce-193">選取發佈點</span><span class="sxs-lookup"><span data-stu-id="d28ce-193">Select a distribution point</span></span>  
 <span data-ttu-id="d28ce-194">若要從伺服器將套件和程式散發到用戶端電腦，您必須先將站台系統指定為發佈點，然後再將套件散發至發佈點。</span><span class="sxs-lookup"><span data-stu-id="d28ce-194">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="d28ce-195">利用下列步驟為您在上一節中建立的 .NET Framework 4.5 套件選取發佈點：</span><span class="sxs-lookup"><span data-stu-id="d28ce-195">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1. <span data-ttu-id="d28ce-196">在 Configuration Manager 主控台中，選擇 [軟體程式庫]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-196">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2. <span data-ttu-id="d28ce-197">在 [軟體程式庫] 工作區中展開 [應用程式管理]，然後選擇 [套件]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-197">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3. <span data-ttu-id="d28ce-198">從套件清單中，選取您在上一節中建立的套件 [.NET Framework 4.5]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-198">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4. <span data-ttu-id="d28ce-199">在 [首頁] 索引標籤的 [部署] 群組中，選擇 [散發內容]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-199">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5. <span data-ttu-id="d28ce-200">在 [散發內容精靈] 的 [一般] 索引標籤上，選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-200">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6. <span data-ttu-id="d28ce-201">在精靈的 [內容目的地] 頁面上，選擇 [新增]，然後選擇 [發佈點]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-201">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7. <span data-ttu-id="d28ce-202">在 [新增發佈點] 對話方塊中，選取要裝載套件和程式的發佈點，然後選擇 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-202">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8. <span data-ttu-id="d28ce-203">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="d28ce-203">Complete the wizard.</span></span>  
  
 <span data-ttu-id="d28ce-204">現在套件中將會包含進行 .NET Framework 4.5 無訊息部署所需的全部資訊。</span><span class="sxs-lookup"><span data-stu-id="d28ce-204">The package now contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="d28ce-205">在您部署套件和程式之前，請先確認它已安裝在發佈點上。請參閱 Configuration Manager 文件庫中[監視您已使用 System Center Configuration Manager 發佈的內容](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed)的＜監視內容＞一節。</span><span class="sxs-lookup"><span data-stu-id="d28ce-205">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Monitor content you have distributed with System Center Configuration Manager](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="d28ce-206">部署套件</span><span class="sxs-lookup"><span data-stu-id="d28ce-206">Deploy the package</span></span>  
 <span data-ttu-id="d28ce-207">若要部署 .NET Framework 4.5 套件和程式：</span><span class="sxs-lookup"><span data-stu-id="d28ce-207">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1. <span data-ttu-id="d28ce-208">在 Configuration Manager 主控台中，選擇 [軟體程式庫]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-208">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2. <span data-ttu-id="d28ce-209">在 [軟體程式庫] 工作區中展開 [應用程式管理]，然後選擇 [套件]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-209">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3. <span data-ttu-id="d28ce-210">從套件清單中，選取您所建立名為 [.NET Framework 4.5] 的套件。</span><span class="sxs-lookup"><span data-stu-id="d28ce-210">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4. <span data-ttu-id="d28ce-211">在 [首頁] 索引標籤的 [部署] 群組中，選擇 [部署]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-211">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5. <span data-ttu-id="d28ce-212">在 [部署軟體精靈] 的 [一般] 頁面上，選擇 [瀏覽]，然後選取您先前建立的集合。</span><span class="sxs-lookup"><span data-stu-id="d28ce-212">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="d28ce-213">選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-213">Choose **Next**.</span></span>  
  
6. <span data-ttu-id="d28ce-214">在精靈的 [內容] 頁面上，確認已顯示軟體的發佈點，然後選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-214">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7. <span data-ttu-id="d28ce-215">在精靈的 [部署設定] 頁面中，確認 [動作] 設定為 [安裝]，且 [用途] 設定為 [必要項]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-215">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="d28ce-216">這樣可確保軟體套件會是目標電腦上的必要安裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-216">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="d28ce-217">選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-217">Choose **Next**.</span></span>  
  
8. <span data-ttu-id="d28ce-218">在精靈的 [排程] 頁面中，指定要安裝 .NET Framework 的時機。</span><span class="sxs-lookup"><span data-stu-id="d28ce-218">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="d28ce-219">您可以選擇 [新增] 指派安裝時間，或是指示軟體在使用者登入或登出時安裝，或是盡快安裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-219">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="d28ce-220">選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-220">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="d28ce-221">在精靈的 [使用者經驗] 頁面上，使用預設值並選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-221">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d28ce-222">您的實際執行環境可能有一些原則，而且這些原則需要不同的部署排程選項。</span><span class="sxs-lookup"><span data-stu-id="d28ce-222">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="d28ce-223">如需這些選項的資訊，請參閱 [Advertisement Name Properties:Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29) (公告名稱屬性：排程索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-223">For information about these options, see [Advertisement Name Properties: Schedule Tab](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).</span></span>
  
10. <span data-ttu-id="d28ce-224">在精靈的 [發佈點] 頁面上，使用預設值並選擇 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d28ce-224">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="d28ce-225">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="d28ce-225">Complete the wizard.</span></span> <span data-ttu-id="d28ce-226">您可以在 [監視] 工作區的 [部署] 節點中監視部署進度。</span><span class="sxs-lookup"><span data-stu-id="d28ce-226">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="d28ce-227">現在套件將會部署至目標集合，而且 .NET Framework 4.5 的無訊息安裝將開始進行。</span><span class="sxs-lookup"><span data-stu-id="d28ce-227">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="d28ce-228">如需 .NET Framework 4.5 安裝錯誤碼的詳細資訊，請參閱本主題稍後的[傳回碼](#return_codes)一節。</span><span class="sxs-lookup"><span data-stu-id="d28ce-228">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="d28ce-229">資源</span><span class="sxs-lookup"><span data-stu-id="d28ce-229">Resources</span></span>  
 <span data-ttu-id="d28ce-230">如需有關測試和部署 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發套件之基礎結構的詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="d28ce-230">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 **<span data-ttu-id="d28ce-231">Active Directory、DNS、DHCP：</span><span class="sxs-lookup"><span data-stu-id="d28ce-231">Active Directory, DNS, DHCP:</span></span>**  
  
-   [<span data-ttu-id="d28ce-232">Active Directory 網域服務</span><span class="sxs-lookup"><span data-stu-id="d28ce-232">Active Directory Domain Services</span></span>](/windows/desktop/ad/active-directory-domain-services)  
  
-   [<span data-ttu-id="d28ce-233">網域名稱系統 (DNS)</span><span class="sxs-lookup"><span data-stu-id="d28ce-233">Domain Name System (DNS)</span></span>](/windows-server/networking/dns/dns-top)  
  
-   [<span data-ttu-id="d28ce-234">動態主機設定通訊協定 (DHCP)</span><span class="sxs-lookup"><span data-stu-id="d28ce-234">Dynamic Host Configuration Protocol (DHCP)</span></span>](/windows-server/networking/technologies/dhcp/dhcp-top)  
  
 **<span data-ttu-id="d28ce-235">SQL Server 2008：</span><span class="sxs-lookup"><span data-stu-id="d28ce-235">SQL Server 2008:</span></span>**  
  
-   [<span data-ttu-id="d28ce-236">安裝 SQL Server 2008 (SQL Server 影片)</span><span class="sxs-lookup"><span data-stu-id="d28ce-236">Installing SQL Server 2008 (SQL Server Video)</span></span>](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))  
  
-   [<span data-ttu-id="d28ce-237">適用於資料庫管理員的 SQL Server 2008 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d28ce-237">SQL Server 2008 Security Overview for Database Administrators</span></span>](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **<span data-ttu-id="d28ce-238">System Center 2012 Configuration Manager (管理點、發佈點)：</span><span class="sxs-lookup"><span data-stu-id="d28ce-238">System Center 2012 Configuration Manager (Management Point, Distribution Point):</span></span>**  
  
-   [<span data-ttu-id="d28ce-239">System Center 2012 Configuration Manager 的網站管理</span><span class="sxs-lookup"><span data-stu-id="d28ce-239">Site Administration for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)  
  
-   [<span data-ttu-id="d28ce-240">Configuration Manager 單一網站規劃與部署</span><span class="sxs-lookup"><span data-stu-id="d28ce-240">Configuration Manager Single Site Planning and Deployment</span></span>](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)  
  
 **<span data-ttu-id="d28ce-241">適用於 Windows 電腦的 System Center 2012 Configuration Manager 用戶端：</span><span class="sxs-lookup"><span data-stu-id="d28ce-241">System Center 2012 Configuration Manager client for Windows computers:</span></span>**  
  
-   [<span data-ttu-id="d28ce-242">部署 System Center 2012 Configuration Manager 的用戶端</span><span class="sxs-lookup"><span data-stu-id="d28ce-242">Deploying Clients for System Center 2012 Configuration Manager</span></span>](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="d28ce-243">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d28ce-243">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="d28ce-244">記錄檔位置</span><span class="sxs-lookup"><span data-stu-id="d28ce-244">Log file locations</span></span>  
 <span data-ttu-id="d28ce-245">在 .NET Framework 安裝過程中會產生下列記錄檔：</span><span class="sxs-lookup"><span data-stu-id="d28ce-245">The following log files are generated during .NET Framework setup:</span></span>  
  
 <span data-ttu-id="d28ce-246">%temp%\Microsoft .NET Framework *版本*\*.txt</span><span class="sxs-lookup"><span data-stu-id="d28ce-246">%temp%\Microsoft .NET Framework *version*\*.txt</span></span>  
 <span data-ttu-id="d28ce-247">%temp%\Microsoft .NET Framework *版本*\*.html</span><span class="sxs-lookup"><span data-stu-id="d28ce-247">%temp%\Microsoft .NET Framework *version*\*.html</span></span>  
  
 <span data-ttu-id="d28ce-248">其中*版本*是您要安裝的 .NET Framework 版本，例如 4.5 或 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="d28ce-248">where *version* is the version of the .NET Framework that you're installing, such as 4.5 or 4.7.2.</span></span>  
 
 <span data-ttu-id="d28ce-249">您也可以使用 .NET Framework 安裝命令中的 `/log` 命令列選項，指定寫入記錄檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="d28ce-249">You can also specify the directory to which log files are written by using the `/log` command-line option in the .NET Framework installation command.</span></span> <span data-ttu-id="d28ce-250">如需詳細資訊，請參閱[開發人員的 .NET Framework 部署指南](deployment-guide-for-developers.md#command-line-options)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-250">For more information, see [.NET Framework deployment guide for developers](deployment-guide-for-developers.md#command-line-options).</span></span> 
 
 <span data-ttu-id="d28ce-251">您可以使用[記錄收集工具](https://www.microsoft.com/download/details.aspx?id=12493)來收集 .NET Framework 記錄檔並建立縮減檔案大小的壓縮封包檔 (.cab)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-251">You can use the [log collection tool](https://www.microsoft.com/download/details.aspx?id=12493) to collect the .NET Framework log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="d28ce-252">傳回碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-252">Return codes</span></span>  
 <span data-ttu-id="d28ce-253">下表列出 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發安裝程式最常見的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="d28ce-253">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="d28ce-254">所有版本的安裝程式的傳回碼都相同。</span><span class="sxs-lookup"><span data-stu-id="d28ce-254">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="d28ce-255">如需詳細資訊的連結，請參閱下一節：[下載錯誤碼](#additional_error_codes)。</span><span class="sxs-lookup"><span data-stu-id="d28ce-255">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="d28ce-256">傳回碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-256">Return code</span></span>|<span data-ttu-id="d28ce-257">說明</span><span class="sxs-lookup"><span data-stu-id="d28ce-257">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d28ce-258">0</span><span class="sxs-lookup"><span data-stu-id="d28ce-258">0</span></span>|<span data-ttu-id="d28ce-259">安裝已順利完成。</span><span class="sxs-lookup"><span data-stu-id="d28ce-259">Installation completed successfully.</span></span>|  
|<span data-ttu-id="d28ce-260">1602</span><span class="sxs-lookup"><span data-stu-id="d28ce-260">1602</span></span>|<span data-ttu-id="d28ce-261">使用者已取消安裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-261">The user canceled installation.</span></span>|  
|<span data-ttu-id="d28ce-262">1603</span><span class="sxs-lookup"><span data-stu-id="d28ce-262">1603</span></span>|<span data-ttu-id="d28ce-263">安裝期間發生嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d28ce-263">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="d28ce-264">1641</span><span class="sxs-lookup"><span data-stu-id="d28ce-264">1641</span></span>|<span data-ttu-id="d28ce-265">需要重新開機才能完成安裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-265">A restart is required to complete the installation.</span></span> <span data-ttu-id="d28ce-266">這個訊息表示成功。</span><span class="sxs-lookup"><span data-stu-id="d28ce-266">This message indicates success.</span></span>|  
|<span data-ttu-id="d28ce-267">3010</span><span class="sxs-lookup"><span data-stu-id="d28ce-267">3010</span></span>|<span data-ttu-id="d28ce-268">需要重新開機才能完成安裝。</span><span class="sxs-lookup"><span data-stu-id="d28ce-268">A restart is required to complete the installation.</span></span> <span data-ttu-id="d28ce-269">這個訊息表示成功。</span><span class="sxs-lookup"><span data-stu-id="d28ce-269">This message indicates success.</span></span>|  
|<span data-ttu-id="d28ce-270">5100</span><span class="sxs-lookup"><span data-stu-id="d28ce-270">5100</span></span>|<span data-ttu-id="d28ce-271">使用者的電腦不符合系統需求。</span><span class="sxs-lookup"><span data-stu-id="d28ce-271">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="d28ce-272">下載錯誤碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-272">Download error codes</span></span>  
  
-   [<span data-ttu-id="d28ce-273">背景智慧型傳送服務 (BITS) 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-273">Background Intelligent Transfer Service (BITS) error codes</span></span>](/windows/desktop/Bits/bits-return-values)  
  
-   [<span data-ttu-id="d28ce-274">URL Moniker 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-274">URL moniker error codes</span></span>](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)  
  
-   [<span data-ttu-id="d28ce-275">WinHttp 錯誤碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-275">WinHttp error codes</span></span>](/windows/desktop/WinHttp/error-messages)  
  
 <span data-ttu-id="d28ce-276">其他錯誤碼：</span><span class="sxs-lookup"><span data-stu-id="d28ce-276">Other error codes:</span></span>  
  
-   [<span data-ttu-id="d28ce-277">Windows 安裝程式錯誤碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-277">Windows Installer error codes</span></span>](/windows/desktop/msi/error-codes)

-   [<span data-ttu-id="d28ce-278">Windows Update 代理程式結果碼</span><span class="sxs-lookup"><span data-stu-id="d28ce-278">Windows Update Agent result codes</span></span>](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a><span data-ttu-id="d28ce-279">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d28ce-279">See also</span></span>

- [<span data-ttu-id="d28ce-280">開發人員部署手冊</span><span class="sxs-lookup"><span data-stu-id="d28ce-280">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)
- [<span data-ttu-id="d28ce-281">系統需求</span><span class="sxs-lookup"><span data-stu-id="d28ce-281">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)
