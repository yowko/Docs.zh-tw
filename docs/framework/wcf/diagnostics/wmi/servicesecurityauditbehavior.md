---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: dc48b8742c60714720be3cf4b22ba672f73c720a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570222"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="ed2e5-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="ed2e5-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="ed2e5-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="ed2e5-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed2e5-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ed2e5-105">方法</span><span class="sxs-lookup"><span data-stu-id="ed2e5-105">Methods</span></span>  
 <span data-ttu-id="ed2e5-106">ServiceSecurityAuditBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ed2e5-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ed2e5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ed2e5-107">Properties</span></span>  
 <span data-ttu-id="ed2e5-108">ServiceSecurityAuditBehavior 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ed2e5-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="ed2e5-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="ed2e5-109">AuditLogLocation</span></span>  
 <span data-ttu-id="ed2e5-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ed2e5-110">Data type: string</span></span>  
  
 <span data-ttu-id="ed2e5-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed2e5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed2e5-112">稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="ed2e5-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="ed2e5-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="ed2e5-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="ed2e5-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ed2e5-114">Data type: string</span></span>  
  
 <span data-ttu-id="ed2e5-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed2e5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed2e5-116">用於記錄稽核事件之訊息驗證等級的類型。</span><span class="sxs-lookup"><span data-stu-id="ed2e5-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="ed2e5-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="ed2e5-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="ed2e5-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ed2e5-118">Data type: string</span></span>  
  
 <span data-ttu-id="ed2e5-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed2e5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed2e5-120">稽核記錄檔中記錄之授權事件的類型。</span><span class="sxs-lookup"><span data-stu-id="ed2e5-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="ed2e5-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="ed2e5-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="ed2e5-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="ed2e5-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ed2e5-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed2e5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed2e5-124">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="ed2e5-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed2e5-125">需求</span><span class="sxs-lookup"><span data-stu-id="ed2e5-125">Requirements</span></span>  
  
|<span data-ttu-id="ed2e5-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ed2e5-126">MOF</span></span>|<span data-ttu-id="ed2e5-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ed2e5-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ed2e5-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="ed2e5-128">Namespace</span></span>|<span data-ttu-id="ed2e5-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="ed2e5-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed2e5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed2e5-130">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
