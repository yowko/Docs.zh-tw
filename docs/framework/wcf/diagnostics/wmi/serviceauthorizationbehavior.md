---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb02a02557a88bf53ca1a8e5b30fe66d6995e545
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="15df0-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="15df0-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="15df0-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="15df0-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15df0-104">語法</span><span class="sxs-lookup"><span data-stu-id="15df0-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="15df0-105">方法</span><span class="sxs-lookup"><span data-stu-id="15df0-105">Methods</span></span>  
 <span data-ttu-id="15df0-106">ServiceAuthorizationBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="15df0-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15df0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="15df0-107">Properties</span></span>  
 <span data-ttu-id="15df0-108">ServiceAuthorizationBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="15df0-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="15df0-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="15df0-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="15df0-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="15df0-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="15df0-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15df0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15df0-112">值，控制服務是否使用傳入訊息所提供的認證來嘗試模擬。</span><span class="sxs-lookup"><span data-stu-id="15df0-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="15df0-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="15df0-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="15df0-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15df0-114">Data type: string</span></span>  
  
 <span data-ttu-id="15df0-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15df0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15df0-116">用於在伺服器上執行作業的原則。</span><span class="sxs-lookup"><span data-stu-id="15df0-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="15df0-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="15df0-117">RoleProvider</span></span>  
 <span data-ttu-id="15df0-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15df0-118">Data type: string</span></span>  
  
 <span data-ttu-id="15df0-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15df0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15df0-120">ASP.NET 角色提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="15df0-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="15df0-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="15df0-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="15df0-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15df0-122">Data type: string</span></span>  
  
 <span data-ttu-id="15df0-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15df0-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15df0-124">用於自訂授權的授權管理員。</span><span class="sxs-lookup"><span data-stu-id="15df0-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15df0-125">需求</span><span class="sxs-lookup"><span data-stu-id="15df0-125">Requirements</span></span>  
  
|<span data-ttu-id="15df0-126">MOF</span><span class="sxs-lookup"><span data-stu-id="15df0-126">MOF</span></span>|<span data-ttu-id="15df0-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="15df0-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="15df0-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="15df0-128">Namespace</span></span>|<span data-ttu-id="15df0-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="15df0-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15df0-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15df0-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
