---
title: 重要的安全性概念
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c483baeca9efcbc4a38020a7b2f4fa221a6b4028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="key-security-concepts"></a>重要的安全性概念
Microsoft.NET Framework 提供以角色為基礎的安全性，以幫助解除對行動程式碼安全性的相關疑慮，並提供支援，讓元件能夠判斷哪些使用者有權執行。  
  
## <a name="type-safety-and-security"></a>類型安全和安全性  
 類型安全程式碼只會存取經授權存取的記憶體位置。 (這裡所討論的類型安全是專指記憶體類型安全，不應與廣義的類型安全混淆。)例如，類型安全程式碼無法從另一個物件的私用欄位讀取值。 它只會以妥善定義、可允許的方式來存取類型。  
  
 在 Just-In-Time (JIT) 編譯期間，選擇性的驗證程序會檢查中繼資料，以及要以 JIT 編譯成原生機器程式碼之方法的 Microsoft Intermediate Language (MSIL)，以驗證其類型安全。 如果程式碼具有略過驗證的權限，則會略過此程序。 如需有關驗證的詳細資訊，請參閱 [Managed 執行程序](../../../docs/standard/managed-execution-process.md)。  
  
 雖然沒有強制要驗證類型安全才能執行 Managed 程式碼，但是在組件隔離和強制執行安全性的作業中，類型安全扮演相當重要的角色。 當程式碼類型安全時，Common Language Runtime 可以將組件彼此完全隔離。 此隔離有助於確保組件無法對彼此產生不利的影響，而且也會增加應用程式的可靠性。 類型安全元件即使受信任的層級不同，還是可以在相同的處理序中安全地執行。 當程式碼不是類型安全時，可能會發生不必要的副作用。 例如，執行階段無法防止 Managed 程式碼呼叫機器碼 (Unmanaged) 及執行惡意的作業。 當程式碼為類型安全時，執行階段的安全性強制機制可確保它不會存取原生程式碼，除非它有這樣的權限。 所有不是類型安全的程式碼，都必須被授與具有通過之列舉成員 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> 的 <xref:System.Security.Permissions.SecurityPermission>，才能執行。  
  
 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../docs/framework/misc/code-access-security-basics.md)。  
  
## <a name="principal"></a>主體  
 主體代表使用者的身分識別與角色，並且會代表使用者採取行動。 在 .NET Framework 中，以角色為基礎的安全性可支援三種主體：  
  
-   泛型主體代表獨立於 Windows 使用者和角色而存在的使用者和角色。  
  
-   Windows 主體代表 Windows 使用者及其角色 (或其 Windows 群組)。 Windows 主體可以模擬另一位使用者，這表示該主體可以代表使用者存取資源，同時呈現屬於該使用者身分識別。  
  
-   自訂主體可以由應用程式以該特定應用程式所需的任何方式來定義。 其可擴充主體身分識別和角色的基本概念。  
  
 如需詳細資訊，請參閱[主體和身分識別物件](../../../docs/standard/security/principal-and-identity-objects.md)。  
  
## <a name="authentication"></a>驗證  
 驗證是探索並確認主體身分識別的程序，它會檢查使用者的認證，並針對某授權單位來驗證那些認證。 在驗證期間取得的資訊可直接供是由您的程式碼使用。 您也可以使用 .NET Framework 以角色為基礎的安全性來驗證目前使用者，以及判斷是否允許該主體存取您的程式碼。 請參閱 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> 方法的多載，以取得如何針對特定角色來驗證主體的範例。 例如，您可以使用 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> 多載來判斷目前使用者是否為系統管理員群組的成員。  
  
 當今所使用的驗證機制非常多樣化，其中有許多可以搭配 .NET Framework 以角色為基礎的安全性。 部分最常用的機制有基本、摘要式、Passport、作業系統 (例如 NTLM 或 Kerberos) 或應用程式定義的機制。  
  
### <a name="example"></a>範例  
 下列範例需要由作用中的主體做為系統管理員。 `name` 參數為 `null`，可讓做為系統管理員的任何使用者傳遞要求。  
  
> [!NOTE]
>  在 Windows Vista 中，使用者帳戶控制 (UAC) 會判斷使用者的權限。 如果您是內建 Administrators 群組的成員，系統會將兩個執行階段存取語彙基元 (Token) 指派給您：標準使用者存取語彙基元及管理員存取語彙基元。 根據預設，您會屬於標準使用者角色。 若要執行需要您是系統管理員的程式碼，您必須先將權限從標準使用者提高為系統管理員。 您可以在啟動應用程式時，以滑鼠右鍵按一下應用程式圖示，並指出您想要以系統管理員身分執行，藉此提高為系統管理員權限。  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 下列範例示範如何判斷主體的身分識別，以及可供主體使用的角色。 此範例的應用程式可能是要確認目前的使用者是您允許使用您的應用程式的角色。  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>授權  
 授權是決定是否允許主體執行所要求動作的程序。 授權會在驗證之後進行，它會使用主體的身分識別和角色相關資訊來判斷主體可以存取哪些資源。 您可以使用 .NET Framework 以角色為基礎的安全性來實作授權。
