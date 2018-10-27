---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: e8b24877c2d76a3f2f90c27ae83374c7bca1328b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181156"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="f72bd-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="f72bd-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="f72bd-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="f72bd-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="f72bd-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f72bd-105">方法</span><span class="sxs-lookup"><span data-stu-id="f72bd-105">Methods</span></span>  
 <span data-ttu-id="f72bd-106">ServiceSecurityAuditBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f72bd-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f72bd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f72bd-107">Properties</span></span>  
 <span data-ttu-id="f72bd-108">ServiceSecurityAuditBehavior 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f72bd-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="f72bd-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="f72bd-109">AuditLogLocation</span></span>  
 <span data-ttu-id="f72bd-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f72bd-110">Data type: string</span></span>  
  
 <span data-ttu-id="f72bd-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f72bd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f72bd-112">稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="f72bd-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="f72bd-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="f72bd-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="f72bd-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f72bd-114">Data type: string</span></span>  
  
 <span data-ttu-id="f72bd-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f72bd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f72bd-116">用於記錄稽核事件之訊息驗證等級的類型。</span><span class="sxs-lookup"><span data-stu-id="f72bd-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="f72bd-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="f72bd-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="f72bd-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f72bd-118">Data type: string</span></span>  
  
 <span data-ttu-id="f72bd-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f72bd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f72bd-120">稽核記錄檔中記錄之授權事件的類型。</span><span class="sxs-lookup"><span data-stu-id="f72bd-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="f72bd-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="f72bd-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="f72bd-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f72bd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f72bd-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f72bd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f72bd-124">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="f72bd-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72bd-125">需求</span><span class="sxs-lookup"><span data-stu-id="f72bd-125">Requirements</span></span>  
  
|<span data-ttu-id="f72bd-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f72bd-126">MOF</span></span>|<span data-ttu-id="f72bd-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f72bd-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f72bd-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="f72bd-128">Namespace</span></span>|<span data-ttu-id="f72bd-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f72bd-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f72bd-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f72bd-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
