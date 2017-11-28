---
title: "在完全信任環境下執行內部網路應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58eeda82c66ecda6ffd714e808b006634ccba804
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="running-intranet-applications-in-full-trust"></a><span data-ttu-id="f808d-102">在完全信任環境下執行內部網路應用程式</span><span class="sxs-lookup"><span data-stu-id="f808d-102">Running Intranet Applications in Full Trust</span></span>
<span data-ttu-id="f808d-103">從 .NET Framework 3.5 版 Service Pack 1 (SP1) 開始，應用程式及其程式庫組件可以當成來自網路共用的完全信任組件執行。</span><span class="sxs-lookup"><span data-stu-id="f808d-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), applications and their library assemblies can be run as full-trust assemblies from a network share.</span></span> <span data-ttu-id="f808d-104"><xref:System.Security.SecurityZone.MyComputer> 區域辨識項會自動新增至從內部網路共用載入的組件。</span><span class="sxs-lookup"><span data-stu-id="f808d-104"><xref:System.Security.SecurityZone.MyComputer> zone evidence is automatically added to assemblies that are loaded from a share on the intranet.</span></span> <span data-ttu-id="f808d-105">這個辨識項會提供這些組件與電腦上組件相同的授權集 (通常為完全信任)。</span><span class="sxs-lookup"><span data-stu-id="f808d-105">This evidence gives those assemblies the same grant set (which is typically full trust) as the assemblies that reside on the computer.</span></span> <span data-ttu-id="f808d-106">此功能不適用於 ClickOnce 應用程式或專為主機設計執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f808d-106">This functionality does not apply to ClickOnce applications or to applications that are designed to run on a host.</span></span>  
  
## <a name="rules-for-library-assemblies"></a><span data-ttu-id="f808d-107">程式庫組件規則</span><span class="sxs-lookup"><span data-stu-id="f808d-107">Rules for Library Assemblies</span></span>  
 <span data-ttu-id="f808d-108">下列規則適用於可執行檔在網路共用上載入的組件：</span><span class="sxs-lookup"><span data-stu-id="f808d-108">The following rules apply to assemblies that are loaded by an executable on a network share:</span></span>  
  
-   <span data-ttu-id="f808d-109">程式庫組件必須和可執行組件位於相同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f808d-109">Library assemblies must reside in the same folder as the executable assembly.</span></span> <span data-ttu-id="f808d-110">完全信任的授權集不提供給位於子資料夾或於不同路徑參考的組件。</span><span class="sxs-lookup"><span data-stu-id="f808d-110">Assemblies that reside in a subfolder or are referenced on a different path are not given the full-trust grant set.</span></span>  
  
-   <span data-ttu-id="f808d-111">如果可執行檔延遲載入組件，即必須使用啟動可執行檔所用的相同路徑。</span><span class="sxs-lookup"><span data-stu-id="f808d-111">If the executable delay-loads an assembly, it must use the same path that was used to start the executable.</span></span> <span data-ttu-id="f808d-112">例如，如果共用 \\\\網路電腦\\共用對應至某個磁碟機代號，而可執行檔是從該路徑執行，則可執行檔使用網路路徑載入的組件將不會具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="f808d-112">For example, if the share \\\\*network-computer*\\*share* is mapped to a drive letter and the executable is run from that path, assemblies that are loaded by the executable by using the network path will not be granted full trust.</span></span> <span data-ttu-id="f808d-113">若要在 <xref:System.Security.SecurityZone.MyComputer> 區域中延遲載入組件，可執行檔必須使用磁碟機代號路徑。</span><span class="sxs-lookup"><span data-stu-id="f808d-113">To delay-load an assembly in the <xref:System.Security.SecurityZone.MyComputer> zone, the executable must use the drive letter path.</span></span>  
  
## <a name="restoring-the-former-intranet-policy"></a><span data-ttu-id="f808d-114">還原先前的內部網路原則</span><span class="sxs-lookup"><span data-stu-id="f808d-114">Restoring the Former Intranet Policy</span></span>  
 <span data-ttu-id="f808d-115">在舊版的 .NET Framework 中，共用的組件被授與 <xref:System.Security.SecurityZone.Intranet> 區域辨識項。</span><span class="sxs-lookup"><span data-stu-id="f808d-115">In earlier versions of the .NET Framework, shared assemblies were granted <xref:System.Security.SecurityZone.Intranet> zone evidence.</span></span> <span data-ttu-id="f808d-116">您必須指定程式碼存取安全性原則，才能授與共用組件完全信任。</span><span class="sxs-lookup"><span data-stu-id="f808d-116">You had to specify code access security policy to grant full trust to an assembly on a share.</span></span>  
  
 <span data-ttu-id="f808d-117">此新行為是內部網路組件的預設值。</span><span class="sxs-lookup"><span data-stu-id="f808d-117">This new behavior is the default for intranet assemblies.</span></span> <span data-ttu-id="f808d-118">您可以設定適用於電腦上所有應用程式的登錄機碼，回到提供 <xref:System.Security.SecurityZone.Intranet> 辨識項的先前行為。</span><span class="sxs-lookup"><span data-stu-id="f808d-118">You can return to the earlier behavior of providing <xref:System.Security.SecurityZone.Intranet> evidence by setting a registry key that applies to all applications on the computer.</span></span> <span data-ttu-id="f808d-119">此程序在 32 位元電腦和 64 位元電腦中是不同的：</span><span class="sxs-lookup"><span data-stu-id="f808d-119">This process is different for 32-bit and 64-bit computers:</span></span>  
  
-   <span data-ttu-id="f808d-120">在 32 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立子機碼。</span><span class="sxs-lookup"><span data-stu-id="f808d-120">On 32-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="f808d-121">使用 DWORD 值為 1 的機碼名稱 LegacyMyComputerZone。</span><span class="sxs-lookup"><span data-stu-id="f808d-121">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span>  
  
-   <span data-ttu-id="f808d-122">在 64 位元電腦系統登錄的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 機碼下，建立子機碼。</span><span class="sxs-lookup"><span data-stu-id="f808d-122">On 64-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="f808d-123">使用 DWORD 值為 1 的機碼名稱 LegacyMyComputerZone。</span><span class="sxs-lookup"><span data-stu-id="f808d-123">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span> <span data-ttu-id="f808d-124">在 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 機碼下建立相同的子機碼。</span><span class="sxs-lookup"><span data-stu-id="f808d-124">Create the same subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f808d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f808d-125">See Also</span></span>  
 [<span data-ttu-id="f808d-126">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="f808d-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
