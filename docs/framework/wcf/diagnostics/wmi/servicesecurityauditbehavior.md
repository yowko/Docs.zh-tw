---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 9da8f77ee8ea5dc8b22ac5c0cb5113e906c5dc78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262264"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="ecc84-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="ecc84-102">ServiceSecurityAuditBehavior</span></span>

<span data-ttu-id="ecc84-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="ecc84-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc84-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ecc84-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ecc84-105">方法</span><span class="sxs-lookup"><span data-stu-id="ecc84-105">Methods</span></span>  

 <span data-ttu-id="ecc84-106">ServiceSecurityAuditBehavior 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ecc84-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ecc84-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ecc84-107">Properties</span></span>  

 <span data-ttu-id="ecc84-108">ServiceSecurityAuditBehavior 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ecc84-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="ecc84-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="ecc84-109">AuditLogLocation</span></span>  

 <span data-ttu-id="ecc84-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="ecc84-110">Data type: string</span></span>  
  
 <span data-ttu-id="ecc84-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ecc84-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecc84-112">稽核記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="ecc84-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="ecc84-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="ecc84-113">MessageAuthenticationAuditLevel</span></span>  

 <span data-ttu-id="ecc84-114">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="ecc84-114">Data type: string</span></span>  
  
 <span data-ttu-id="ecc84-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ecc84-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecc84-116">用於記錄稽核事件之訊息驗證等級的類型。</span><span class="sxs-lookup"><span data-stu-id="ecc84-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="ecc84-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="ecc84-117">ServiceAuthorizationAuditLevel</span></span>  

 <span data-ttu-id="ecc84-118">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="ecc84-118">Data type: string</span></span>  
  
 <span data-ttu-id="ecc84-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ecc84-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecc84-120">稽核記錄檔中記錄之授權事件的類型。</span><span class="sxs-lookup"><span data-stu-id="ecc84-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="ecc84-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="ecc84-121">SuppressAuditFailure</span></span>  

 <span data-ttu-id="ecc84-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="ecc84-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ecc84-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ecc84-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecc84-124">布林值，指定隱藏寫入稽核記錄檔錯誤的行為。</span><span class="sxs-lookup"><span data-stu-id="ecc84-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc84-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="ecc84-125">Requirements</span></span>  
  
|<span data-ttu-id="ecc84-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ecc84-126">MOF</span></span>|<span data-ttu-id="ecc84-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ecc84-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ecc84-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="ecc84-128">Namespace</span></span>|<span data-ttu-id="ecc84-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="ecc84-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecc84-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecc84-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
