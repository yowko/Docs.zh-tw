---
title: 安全性和序列化
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0b1f8979929dbb6872bbd53e1840b2d0520a31d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910664"
---
# <a name="security-and-serialization"></a><span data-ttu-id="ca01b-102">安全性和序列化</span><span class="sxs-lookup"><span data-stu-id="ca01b-102">Security and Serialization</span></span>
<span data-ttu-id="ca01b-103">由於序列化可允許其他程式碼看到或修改在其他情況下無法存取的物件執行個體資料，因此執行序列化的程式碼需要特殊權限： <xref:System.Security.Permissions.SecurityPermission> ，並指定 <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> 旗標。</span><span class="sxs-lookup"><span data-stu-id="ca01b-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="ca01b-104">依照預設原則，這個使用權限不會授與給網際網路下載或內部網路的程式碼；只有本機電腦上的程式碼才會被授與這個使用權限。</span><span class="sxs-lookup"><span data-stu-id="ca01b-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="ca01b-105">通常會序列化物件執行個體的所有欄位，這表示資料會以執行個體的序列化資料來代表。</span><span class="sxs-lookup"><span data-stu-id="ca01b-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="ca01b-106">可以解譯格式的程式碼可以判斷資料值，而不論成員能否存取。</span><span class="sxs-lookup"><span data-stu-id="ca01b-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="ca01b-107">同樣地，還原序列化會從序列化表示法中擷取資料，並直接設定物件狀態，這同樣也不受存取能力規則的影響。</span><span class="sxs-lookup"><span data-stu-id="ca01b-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="ca01b-108">如果可能的話，可能含有安全性顧慮資料的物件都應該設為不可序列化。</span><span class="sxs-lookup"><span data-stu-id="ca01b-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="ca01b-109">如果必須是可序列化，請嘗試讓保存機密資料的特定欄位不可序列化。</span><span class="sxs-lookup"><span data-stu-id="ca01b-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="ca01b-110">如果無法完成，請了解此資料將會公開給具有序列化權限的任何程式碼，並請確定沒有惡意程式碼可以取得此權限。</span><span class="sxs-lookup"><span data-stu-id="ca01b-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="ca01b-111"><xref:System.Runtime.Serialization.ISerializable> 介面只應該由序列化基礎結構所使用。</span><span class="sxs-lookup"><span data-stu-id="ca01b-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="ca01b-112">不過，如果未受保護，它可能會釋出機密資訊。</span><span class="sxs-lookup"><span data-stu-id="ca01b-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="ca01b-113">如果您藉由實作 ISerializable **M:System.Runtime.Serialization.ISerializable.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)** 提供自訂序列化，請確認您採取下列預防措施：</span><span class="sxs-lookup"><span data-stu-id="ca01b-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="ca01b-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法應該藉著要求 **SecurityPermission** 並指定 **SerializationFormatter** 權限，或是確定不會隨著方法輸出釋出任何機密資訊，明確地進行保護。</span><span class="sxs-lookup"><span data-stu-id="ca01b-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="ca01b-115">例如：</span><span class="sxs-lookup"><span data-stu-id="ca01b-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="ca01b-116">用於序列化的特殊建構函式也應該執行徹底的輸入驗證，並且應該為受保護或私用，協助防範惡意程式碼的濫用。</span><span class="sxs-lookup"><span data-stu-id="ca01b-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="ca01b-117">它應該強制執行以其他方式 (例如明確建立類別或透過某種處理站間接建立) 取得這種類別的執行個體時，相同的安全性檢查和必要權限。</span><span class="sxs-lookup"><span data-stu-id="ca01b-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca01b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca01b-118">See also</span></span>

- [<span data-ttu-id="ca01b-119">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="ca01b-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
