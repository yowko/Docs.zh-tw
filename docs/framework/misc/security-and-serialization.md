---
title: 安全性和序列化
description: 閱讀安全性和序列化的相關資訊。 使用 SecurityPermission 搭配指定的 SerializationFormatter 旗標，以查看或修改物件實例資料。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: f19641ad2154631b4eab5104252c12b73b9084fd
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309270"
---
# <a name="security-and-serialization"></a><span data-ttu-id="65f5f-104">安全性和序列化</span><span class="sxs-lookup"><span data-stu-id="65f5f-104">Security and serialization</span></span>

<span data-ttu-id="65f5f-105">由於序列化可允許其他程式碼看到或修改在其他情況下無法存取的物件執行個體資料，因此執行序列化的程式碼需要特殊權限： <xref:System.Security.Permissions.SecurityPermission> ，並指定 <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> 旗標。</span><span class="sxs-lookup"><span data-stu-id="65f5f-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="65f5f-106">依照預設原則，這個使用權限不會授與給網際網路下載或內部網路的程式碼；只有本機電腦上的程式碼才會被授與這個使用權限。</span><span class="sxs-lookup"><span data-stu-id="65f5f-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="65f5f-107">通常會序列化物件執行個體的所有欄位，這表示資料會以執行個體的序列化資料來代表。</span><span class="sxs-lookup"><span data-stu-id="65f5f-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="65f5f-108">可以解譯格式的程式碼可以判斷資料值，而不論成員能否存取。</span><span class="sxs-lookup"><span data-stu-id="65f5f-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="65f5f-109">同樣地，還原序列化會從序列化表示法中擷取資料，並直接設定物件狀態，這同樣也不受存取能力規則的影響。</span><span class="sxs-lookup"><span data-stu-id="65f5f-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="65f5f-110">如果可能的話，可能含有安全性顧慮資料的物件都應該設為不可序列化。</span><span class="sxs-lookup"><span data-stu-id="65f5f-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="65f5f-111">如果必須是可序列化，請嘗試讓保存機密資料的特定欄位不可序列化。</span><span class="sxs-lookup"><span data-stu-id="65f5f-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="65f5f-112">如果無法將這些欄位設為不可序列化，則會對具有序列化許可權的任何程式碼公開敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="65f5f-112">If those fields cannot be made nonserializable, the sensitive data will be exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="65f5f-113">請確定沒有惡意程式碼可以取得此許可權。</span><span class="sxs-lookup"><span data-stu-id="65f5f-113">Make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="65f5f-114"><xref:System.Runtime.Serialization.ISerializable> 介面只應該由序列化基礎結構所使用。</span><span class="sxs-lookup"><span data-stu-id="65f5f-114">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="65f5f-115">不過，如果未受保護，它可能會釋出機密資訊。</span><span class="sxs-lookup"><span data-stu-id="65f5f-115">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="65f5f-116">如果您藉由實作 ISerializable **M:System.Runtime.Serialization.ISerializable.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)** 提供自訂序列化，請確認您採取下列預防措施：</span><span class="sxs-lookup"><span data-stu-id="65f5f-116">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="65f5f-117"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法應該藉著要求 **SecurityPermission** 並指定 **SerializationFormatter** 權限，或是確定不會隨著方法輸出釋出任何機密資訊，明確地進行保護。</span><span class="sxs-lookup"><span data-stu-id="65f5f-117">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="65f5f-118">例如：</span><span class="sxs-lookup"><span data-stu-id="65f5f-118">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter
    =true)]  
    public override void GetObjectData(SerializationInfo info,
    StreamingContext context)  
    {  
    }  
    ```  
  
- <span data-ttu-id="65f5f-119">用於序列化的特殊建構函式也應該執行徹底的輸入驗證，並且應該為受保護或私用，協助防範惡意程式碼的濫用。</span><span class="sxs-lookup"><span data-stu-id="65f5f-119">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="65f5f-120">它應該強制執行以其他方式 (例如明確建立類別或透過某種處理站間接建立) 取得這種類別的執行個體時，相同的安全性檢查和必要權限。</span><span class="sxs-lookup"><span data-stu-id="65f5f-120">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f5f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f5f-121">See also</span></span>

- [<span data-ttu-id="65f5f-122">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="65f5f-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
