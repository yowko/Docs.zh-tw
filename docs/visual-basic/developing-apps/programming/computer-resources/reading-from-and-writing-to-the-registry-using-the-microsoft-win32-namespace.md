---
title: 使用 Microsoft.Win32 命名空間讀取和寫入登錄 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: bf0d6ae329c5a09986a4a7bf641fe6820387ff22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916562"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="f667e-102">使用 Microsoft.Win32 命名空間讀取和寫入登錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f667e-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="f667e-103">雖然 `My.Computer.Registry` 應該會涵蓋對登錄進行程式設計時的基本需求，但是您也可以使用 .NET Framework <xref:Microsoft.Win32> 命名空間中的 <xref:Microsoft.Win32.Registry> 和 <xref:Microsoft.Win32.RegistryKey> 類別。</span><span class="sxs-lookup"><span data-stu-id="f667e-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="f667e-104">登錄類別中的機碼</span><span class="sxs-lookup"><span data-stu-id="f667e-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="f667e-105"><xref:Microsoft.Win32.Registry> 類別提供可用來存取子機碼和其值的基底登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f667e-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="f667e-106">基底機碼本身是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f667e-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="f667e-107">下表列出並描述 <xref:Microsoft.Win32.Registry> 類別所公開的七個機碼。</span><span class="sxs-lookup"><span data-stu-id="f667e-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="f667e-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="f667e-108">**Key**</span></span>|<span data-ttu-id="f667e-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="f667e-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="f667e-110">定義文件類型以及與這些類型相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="f667e-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="f667e-111">包含非使用者特定的硬體組態資訊。</span><span class="sxs-lookup"><span data-stu-id="f667e-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="f667e-112">包含目前使用者偏好設定的相關資訊 (例如環境變數)。</span><span class="sxs-lookup"><span data-stu-id="f667e-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="f667e-113">包含動態登錄資料 (例如虛擬裝置驅動程式所使用的動態登錄資料)。</span><span class="sxs-lookup"><span data-stu-id="f667e-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="f667e-114">包含五個子機碼 (Hardware、SAM、Security、Software 和 System) 來保存本機電腦的組態資料。</span><span class="sxs-lookup"><span data-stu-id="f667e-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="f667e-115">包含軟體元件的效能資訊。</span><span class="sxs-lookup"><span data-stu-id="f667e-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="f667e-116">包含預設使用者偏好設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f667e-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="f667e-117">將資料寫入目前使用者 (<xref:Microsoft.Win32.Registry.CurrentUser>)，比寫入本機電腦 (<xref:Microsoft.Win32.Registry.LocalMachine>) 更為安全。</span><span class="sxs-lookup"><span data-stu-id="f667e-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="f667e-118">其他處理序 (可能為惡意) 先前已建立過您正在建立的機碼時，會發生一般稱為「佔用」的情況。</span><span class="sxs-lookup"><span data-stu-id="f667e-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="f667e-119">若要避免發生此問題，請使用 <xref:Microsoft.Win32.RegistryKey.GetValue%2A> 這類方法，以在還沒有索引鍵時傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="f667e-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="f667e-120">讀取登錄中的值</span><span class="sxs-lookup"><span data-stu-id="f667e-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="f667e-121">下列程式碼示範如何讀取 HKEY_CURRENT_USER 中的字串。</span><span class="sxs-lookup"><span data-stu-id="f667e-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="f667e-122">下列程式碼會依序讀取字串、遞增字串，以及將字串寫入 HKEY_CURRENT_USER。</span><span class="sxs-lookup"><span data-stu-id="f667e-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="f667e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f667e-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="f667e-124">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="f667e-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="f667e-125">讀取和寫入登錄</span><span class="sxs-lookup"><span data-stu-id="f667e-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="f667e-126">安全性和登錄</span><span class="sxs-lookup"><span data-stu-id="f667e-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
