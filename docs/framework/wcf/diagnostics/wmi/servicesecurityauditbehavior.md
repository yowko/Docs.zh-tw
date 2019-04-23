---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979130"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="30787-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="30787-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="30787-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="30787-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30787-104">語法</span><span class="sxs-lookup"><span data-stu-id="30787-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="30787-105">方法</span><span class="sxs-lookup"><span data-stu-id="30787-105">Methods</span></span>  
 <span data-ttu-id="30787-106">ServiceSecurityAuditBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="30787-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="30787-107">屬性</span><span class="sxs-lookup"><span data-stu-id="30787-107">Properties</span></span>  
 <span data-ttu-id="30787-108">ServiceSecurityAuditBehavior 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="30787-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="30787-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="30787-109">AuditLogLocation</span></span>  
 <span data-ttu-id="30787-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="30787-110">Data type: string</span></span>  
  
 <span data-ttu-id="30787-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="30787-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30787-112">稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="30787-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="30787-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="30787-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="30787-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="30787-114">Data type: string</span></span>  
  
 <span data-ttu-id="30787-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="30787-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30787-116">用於記錄稽核事件之訊息驗證等級的類型。</span><span class="sxs-lookup"><span data-stu-id="30787-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="30787-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="30787-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="30787-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="30787-118">Data type: string</span></span>  
  
 <span data-ttu-id="30787-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="30787-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30787-120">稽核記錄檔中記錄之授權事件的類型。</span><span class="sxs-lookup"><span data-stu-id="30787-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="30787-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="30787-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="30787-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="30787-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="30787-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="30787-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30787-124">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="30787-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30787-125">需求</span><span class="sxs-lookup"><span data-stu-id="30787-125">Requirements</span></span>  
  
|<span data-ttu-id="30787-126">MOF</span><span class="sxs-lookup"><span data-stu-id="30787-126">MOF</span></span>|<span data-ttu-id="30787-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="30787-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="30787-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="30787-128">Namespace</span></span>|<span data-ttu-id="30787-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="30787-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30787-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30787-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
