---
title: "Key Security Concepts | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "unauthorized access"
  - "permissions [.NET Framework]"
  - "security [.NET Framework], about security"
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: 22
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# Key Security Concepts
Microsoft.NET Framework 提供安全性透明度、程式碼存取安全性，以及以角色為基礎的安全性，以幫助解除對行動程式碼安全性的相關疑慮，並提供支援，讓元件能夠判斷哪些使用者有權執行。  這些安全性機制使用簡單且一致的模型，讓熟悉程式碼存取安全性的開發人員能夠輕鬆使用以角色為基礎的安全性，反之亦然。  程式碼存取安全性和以角色為基礎的安全性都是使用 Common Language Runtime 提供的通用基礎結構來實作。  
  
> [!NOTE]
>  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，安全性透明度為預設的強制機制。  安全性透明度將當成應用程式一部分來執行的程式碼，與當成基礎結構一部分來執行的程式碼分開。  如需詳細資訊，請參閱[Security\-Transparent Code](../../../docs/framework/misc/security-transparent-code.md)。  
  
 由於程式碼存取安全性和以角色為基礎的安全性使用相同的模型和基礎結構，因此它們共用數項基礎概念，本節會有詳細說明。  請確定您已經熟悉這些概念之後，再閱讀 .NET Framework 程式碼存取安全性和以角色為基礎的安全性的文件。  
  
## 安全性權限  
 Common Language Runtime 僅允許程式碼執行該程式碼有權執行的那些作業。  執行階段會使用稱為權限的物件，對 Managed 程式碼強加限制。  執行階段在數個命名空間中提供內建權限類別，並且也支援設計和實作自訂權限類別。  
  
 權限分為兩種，每一種都有特定的用途：  
  
-   程式碼存取權限可讓您存取受保護的資源，或是執行受保護的作業。  
  
-   以角色為基礎的安全性權限會提供一項機制，讓您探索某位使用者 \(或代表使用者運作的代理程式\) 是否具有特定識別或屬於指定角色的成員。  <xref:System.Security.Permissions.PrincipalPermission> 是唯一以角色為基礎的安全性權限。  
  
 安全性權限可以是權限類別的形式 \(命令式安全性\)，或是代表權限類別的屬性 \(宣告式安全性\)。  安全性權限的基底類別是 <xref:System.Security.CodeAccessPermission?displayProperty=fullName>；安全性權限屬性的基底類別是 <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>。  
  
 在將組件形式的應用程式載入應用程式定義域中時，會授與其一組權限。  這些權限通常是使用 <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName> 方法所決定的預先定義權限集合來授與。  授權集會判斷程式碼可供其使用的權限。  執行階段會根據程式碼的原始位置 \(例如，本機電腦、近端內部網路或網際網路\) 來授與權限。  如果程式碼是載入沙箱中，也可以授與特殊權限給程式碼。  如需在沙箱中執行程式碼的詳細資訊，請參閱 [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)。  
  
 權限的主要用途如下所示：  
  
-   程式庫程式碼可以要求其呼叫端必須具備特定的權限。  如果您將權限的 <xref:System.Security.CodeAccessPermission.Demand%2A> 放在程式碼中，使用您的程式碼的所有程式碼，都應該要有該權限才能執行。  要求可以用來判斷呼叫端是否有權存取特定資源，或探索呼叫端的身分識別。  
  
-   程式碼可以使用權限來拒絕存取其想要保護的資源。  您可以使用 <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> 來指定一組有限的權限，以隱含的方式拒絕所有其他權限。  不過，我們不建議為了防範刻意誤用，而使用 <xref:System.Security.Permissions.SecurityAction> 來禁止存取。  被呼叫的組件 \(其授權集中有被隱含拒絕的權限\) 可以針對其想要使用的任何權限執行 <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>，以覆寫被拒絕的權限。  例如，如果您只允許 <xref:System.Security.Permissions.UIPermission>，並呼叫本來就具有 <xref:System.Security.Permissions.FileIOPermission> 的組件，該組件只要針對 <xref:System.Security.Permissions.FileIOPermission> 進行 <xref:System.Security.Permissions.SecurityAction>，並執行檔案作業即可。  若要保護資源安全，不要讓參考組件中不受信任的程式碼存取，唯一的方法就是使用不包含那些權限的授權集來執行該程式碼。  
  
### 程式碼存取權限  
 程式碼存取權限是用來幫助防止未經授權使用資源和作業的權限物件。  其為 Common Language Runtime 在 Managed 程式碼上強制執行安全性限制時，所使用之機制的基礎部分。  
  
 每個程式碼存取權限各代表下列其中一個權限：  
  
-   存取受保護資源 \(例如檔案或環境變數\) 的權限。  
  
-   執行受保護作業 \(例如存取 Unmanaged 程式碼\) 的權限。  
  
 所有程式碼存取權限都可以透過程式碼來要求，執行階段會決定要將哪些權限 \(若有的話\) 授與程式碼。  
  
 每個程式碼存取權限都是衍生自 <xref:System.Security.CodeAccessPermission> 類別，這表示所有程式碼存取權限都有共同的方法，例如 **Demand**、**Assert**、**Deny**、**PermitOnly**、**IsSubsetOf**、**Intersect** 和 **Union**。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，已移除執行階段支援，以強制執行 <xref:System.Security.Permissions.SecurityAction>、<xref:System.Security.Permissions.SecurityAction>、<xref:System.Security.Permissions.SecurityAction> 和 <xref:System.Security.Permissions.SecurityAction> 權限要求。  在以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 或更新版本為基礎的程式碼中，不應使用這些要求。  如需這項變更和其他變更的詳細資訊，請參閱 [安全性變更](../../../docs/framework/security/security-changes.md)。  
  
### 以角色為基礎的安全性權限  
 <xref:System.Security.Permissions.PrincipalPermission> 是以角色為基礎的安全性權限，可以用來判斷使用者是否具有指定的身分識別，或者為指定角色的成員。  **PrincipalPermission** 是 .NET Framework 類別庫提供的唯一以角色為基礎的安全性權限。  
  
## 類型安全和安全性  
 類型安全程式碼只會存取經授權存取的記憶體位置。  \(這裡所討論的類型安全是專指記憶體類型安全，不應與廣義的類型安全混淆。\) 例如，類型安全程式碼無法從另一個物件的私用欄位讀取值。  它只會以妥善定義、可允許的方式來存取類型。  
  
 在 Just\-In\-Time \(JIT\) 編譯期間，選擇性的驗證程序會檢查中繼資料，以及要以 JIT 編譯成原生機器程式碼之方法的 Microsoft Intermediate Language \(MSIL\)，以驗證其類型安全。  如果程式碼具有略過驗證的權限，則會略過此程序。  如需有關驗證的詳細資訊，請參閱 [Managed 執行程序](../../../docs/standard/managed-execution-process.md)。  
  
 雖然沒有強制要驗證類型安全才能執行 Managed 程式碼，但是在組件隔離和強制執行安全性的作業中，類型安全扮演相當重要的角色。  當程式碼類型安全時，Common Language Runtime 可以將組件彼此完全隔離。  此隔離有助於確保組件無法對彼此產生不利的影響，而且也會增加應用程式的可靠性。  類型安全元件即使受信任的層級不同，還是可以在相同的處理序中安全地執行。  當程式碼不是類型安全時，可能會發生不必要的副作用。  例如，執行階段無法防止 Managed 程式碼呼叫機器碼 \(Unmanaged\) 及執行惡意的作業。  當程式碼為類型安全時，執行階段的安全性強制機制可確保它不會存取原生程式碼，除非它有這樣的權限。  所有不是類型安全的程式碼，都必須被授與具有通過之列舉成員 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> 的 <xref:System.Security.Permissions.SecurityPermission>，才能執行。  
  
 如需詳細資訊，請參閱[NIB: Writing Verifiably Type\-Safe Code](http://msdn.microsoft.com/zh-tw/d18f10ef-3b48-4f47-8726-96714021547b)。  
  
## 主體  
 主體代表使用者的身分識別與角色，並且會代表使用者採取行動。  在 .NET Framework 中，以角色為基礎的安全性可支援三種主體：  
  
-   泛型主體代表獨立於 Windows 使用者和角色而存在的使用者和角色。  
  
-   Windows 主體代表 Windows 使用者及其角色 \(或其 Windows 群組\)。  Windows 主體可以模擬另一位使用者，這表示該主體可以代表使用者存取資源，同時呈現屬於該使用者身分識別。  
  
-   自訂主體可以由應用程式以該特定應用程式所需的任何方式來定義。  其可擴充主體身分識別和角色的基本概念。  
  
 如需詳細資訊，請參閱[Principal and Identity Objects](../../../docs/standard/security/principal-and-identity-objects.md)。  
  
## 驗證  
 驗證是探索並確認主體身分識別的程序，它會檢查使用者的認證，並針對某授權單位來驗證那些認證。  在驗證期間取得的資訊可直接供是由您的程式碼使用。  您也可以使用 .NET Framework 以角色為基礎的安全性來驗證目前使用者，以及判斷是否允許該主體存取您的程式碼。  請參閱 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=fullName> 方法的多載，以取得如何針對特定角色來驗證主體的範例。  例如，您可以使用 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=fullName> 多載來判斷目前使用者是否為系統管理員群組的成員。  
  
 當今所使用的驗證機制非常多樣化，其中有許多可以搭配 .NET Framework 以角色為基礎的安全性。  部分最常用的機制有基本、摘要式、Passport、作業系統 \(例如 NTLM 或 Kerberos\) 或應用程式定義的機制。  
  
### 範例  
 下列範例需要由作用中的主體做為系統管理員。  `name` 參數為 `null`，可讓做為系統管理員的任何使用者傳遞要求。  
  
> [!NOTE]
>  在 Windows Vista 中，使用者帳戶控制 \(UAC\) 會判斷使用者的權限。  如果您是內建 Administrators 群組的成員，系統會將兩個執行階段存取語彙基元 \(Token\) 指派給您：標準使用者存取語彙基元及管理員存取語彙基元。  根據預設，您會屬於標準使用者角色。  若要執行需要您是系統管理員的程式碼，您必須先將權限從標準使用者提高為系統管理員。  您可以在啟動應用程式時，以滑鼠右鍵按一下應用程式圖示，並指出您想要以系統管理員身分執行，藉此提高為系統管理員權限。  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 下列範例示範如何判斷主體的身分識別，以及可供主體使用的角色。  此範例的應用程式可能是要確認目前的使用者是您允許使用您的應用程式的角色。  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## 授權  
 授權是決定是否允許主體執行所要求動作的程序。  授權會在驗證之後進行，它會使用主體的身分識別和角色相關資訊來判斷主體可以存取哪些資源。  您可以使用 .NET Framework 以角色為基礎的安全性來實作授權。  
  
## internal virtual 關鍵字的安全性考量  
 請絕不要以在 C\# 中標示 [internal](../Topic/internal%20\(C%23%20Reference\).md) [virtual](../Topic/virtual%20\(C%23%20Reference\).md) 修飾詞 \(在 Visual Basic 中為 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md) [Friend](../Topic/Friend%20\(Visual%20Basic\).md) 修飾詞\) 的成員，做為您應用程式安全性的基礎。  雖然標示這些修飾詞的成員只能被目前組件中的其他成員覆寫，但是只有 C\# 和 Visual Basic 語言會強制執行此規則。  執行階段不會強制執行此規則。  因此，使用 Microsoft Intermediate Language，或是不會強制執行此規則的任何其他語言，都有可能會覆寫在 C\# 中標示為 **internal virtual** 以及在 Visual Basic 中標示為 **Overloads Overridable Friend** 的成員。  
  
## 請參閱  
 [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md)