---
title: 在 ASP.NET 中使用 System.Transactions
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 7b73ec970776f39a0c056e2a706d4818cda6cd72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417616"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="bcfc1-102">在 ASP.NET 中使用 System.Transactions</span><span class="sxs-lookup"><span data-stu-id="bcfc1-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="bcfc1-103">本主題說明如何成功運用 <xref:System.Transactions> 應用程式中的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="bcfc1-104">啟用 ASP.NET 中的 DistributedTransactionPermission</span><span class="sxs-lookup"><span data-stu-id="bcfc1-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="bcfc1-105"><xref:System.Transactions> 支援部分信任的呼叫端，並且含有 **AllowPartiallyTrustedCallers** 屬性 (APTCA) 標記。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="bcfc1-106"><xref:System.Transactions> 會依據 <xref:System.Transactions> 所公開的資源型別 (例如，系統記憶體、共用的整個處理序資源、整個系統資源與其他資源)，以及存取這些資源時必要的信任層級來共同定義信任層級。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="bcfc1-107">在部分信任的環境中，非完整信任組件只能使用應用程式定義域內的交易 (在此情況下，系統記憶體是唯一受保護的資源)，除非它被授予了 <xref:System.Transactions.DistributedTransactionPermission>。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="bcfc1-108">每當交易的管理擴大至需由「Microsoft 分散式交易協調器」(MSDTC) 管理的情況時，就會要求<xref:System.Transactions.DistributedTransactionPermission> 。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="bcfc1-109">這種情況會使用整個處理序的資源，特別是全域資源 (亦即在 MSDTC 記錄中保留的空格)。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="bcfc1-110">資料庫的 Web 前端或是將資料庫當成所提供的服務一部分來使用的應用程式，都是這類用法的例子。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="bcfc1-111"> 擁有專屬的信任層級，並透過原則檔將這些信任層級關聯至特定的權限。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-111"> has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="bcfc1-112">如需詳細資訊，請參閱 < [ASP.NET 信任 Levels and Policy Files](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span></span> <span data-ttu-id="bcfc1-113">在您初次安裝 Windows SDK 時，沒有任何預設的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 原則檔會與 <xref:System.Transactions.DistributedTransactionPermission>關聯。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="bcfc1-114">因此，當 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式中的交易規模擴大至需由 MSDTC 管理時，在要求 <xref:System.Security.SecurityException> 時，擴大規模會失敗，並傳回 <xref:System.Transactions.DistributedTransactionPermission>。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="bcfc1-115">若要在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 部分信任環境中啟用交易擴大規模，您應該在同一個預設信任層級中授與 <xref:System.Transactions.DistributedTransactionPermission> 權限 (與在 <xref:System.Data.SqlClient.SqlClientPermission>中所授與的權限一樣)。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="bcfc1-116">您可以選擇設定自訂的信任層級與原則檔來支援這項作業，或者也可以修改預設的原則檔，亦即 **Web_hightrust.config** 和 **Web_mediumtrust.config**。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="bcfc1-117">若要修改原則檔，請新增**Distributedtransactionpermission**項目**DistributedTransactionPermission**來**Policylevel**項目底下**Securityclasses**項目並將對應**IPermission**項目底下[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** system.transactions。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="bcfc1-118">下列組態檔示範如何進行。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-118">The following configuration file demonstrates this.</span></span>  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 <span data-ttu-id="bcfc1-119">如需詳細資訊[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]安全性原則，請參閱 < [securityPolicy 項目 （ASP.NET 設定結構描述）](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-119">For more information about [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="bcfc1-120">動態編譯</span><span class="sxs-lookup"><span data-stu-id="bcfc1-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="bcfc1-121">如果您希望匯入並使用 <xref:System.Transactions> 應用程式中的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] (在存取時動態編譯)，您可以在組態檔中放置 <xref:System.Transactions> 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="bcfc1-122">具體來說，您應該將參考加入預設根 **Web.config**/**compilation** / **assemblies** 區段底下。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="bcfc1-123">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-123">The following example demonstrates this.</span></span>  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 <span data-ttu-id="bcfc1-124">如需詳細資訊，請參閱 < [（ASP.NET 設定結構描述） 的組件的 add 項目](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4)。</span><span class="sxs-lookup"><span data-stu-id="bcfc1-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/602197e8-108d-4249-b752-ba2a318f75e4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfc1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcfc1-125">See Also</span></span>  
 [<span data-ttu-id="bcfc1-126">ASP.NET Trust Levels and Policy Files</span><span class="sxs-lookup"><span data-stu-id="bcfc1-126">ASP.NET Trust Levels and Policy Files</span></span>](https://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [<span data-ttu-id="bcfc1-127">securityPolicy 項目 （ASP.NET 設定結構描述）</span><span class="sxs-lookup"><span data-stu-id="bcfc1-127">securityPolicy Element (ASP.NET Settings Schema)</span></span>](https://msdn.microsoft.com/library/469d8d22-d263-46bb-8400-40d8d027faba)  
 [<span data-ttu-id="bcfc1-128">異動管理擴大規模</span><span class="sxs-lookup"><span data-stu-id="bcfc1-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)
