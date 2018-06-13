---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485891"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="83e30-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="83e30-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="83e30-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="83e30-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e30-104">語法</span><span class="sxs-lookup"><span data-stu-id="83e30-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="83e30-105">方法</span><span class="sxs-lookup"><span data-stu-id="83e30-105">Methods</span></span>  
 <span data-ttu-id="83e30-106">ServiceSecurityAuditBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="83e30-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="83e30-107">屬性</span><span class="sxs-lookup"><span data-stu-id="83e30-107">Properties</span></span>  
 <span data-ttu-id="83e30-108">ServiceSecurityAuditBehavior 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="83e30-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="83e30-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="83e30-109">AuditLogLocation</span></span>  
 <span data-ttu-id="83e30-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="83e30-110">Data type: string</span></span>  
  
 <span data-ttu-id="83e30-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83e30-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83e30-112">稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="83e30-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="83e30-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="83e30-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="83e30-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="83e30-114">Data type: string</span></span>  
  
 <span data-ttu-id="83e30-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83e30-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83e30-116">用於記錄稽核事件之訊息驗證等級的類型。</span><span class="sxs-lookup"><span data-stu-id="83e30-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="83e30-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="83e30-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="83e30-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="83e30-118">Data type: string</span></span>  
  
 <span data-ttu-id="83e30-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83e30-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83e30-120">稽核記錄檔中記錄之授權事件的類型。</span><span class="sxs-lookup"><span data-stu-id="83e30-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="83e30-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="83e30-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="83e30-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="83e30-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="83e30-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="83e30-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="83e30-124">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="83e30-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e30-125">需求</span><span class="sxs-lookup"><span data-stu-id="83e30-125">Requirements</span></span>  
  
|<span data-ttu-id="83e30-126">MOF</span><span class="sxs-lookup"><span data-stu-id="83e30-126">MOF</span></span>|<span data-ttu-id="83e30-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="83e30-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="83e30-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="83e30-128">Namespace</span></span>|<span data-ttu-id="83e30-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="83e30-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83e30-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83e30-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
