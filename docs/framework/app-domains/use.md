---
title: "使用應用程式定義域"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b2dac2238ae9117d3678335748c680d594a8b5c6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="using-application-domains"></a>使用應用程式定義域
應用程式定義域為 Common Language Runtime 提供隔離單位。 它們是在處理序內建立和執行。 應用程式定義域通常是由執行階段主機所建立，這是負責將執行階段載入處理序以及在應用程式定義域中執行使用者程式碼的應用程式。 執行階段主機會建立處理序和預設的應用程式定義域，在內部執行 Managed 程式碼。 執行階段主機包括 ASP.NET、Microsoft Internet Explorer 和 Windows 殼層。  
  
 大部分的應用程式不需要建立自己的應用程式定義域，執行階段主機會為您建立任何必要的應用程式定義域。 但如果您的應用程式需要隔離程式碼或使用及卸載 DLL，您可以建立及設定其他應用程式定義域。  
  
## <a name="in-this-section"></a>本章節內容  
 [操作說明：建立應用程式定義域](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 描述如何以程式設計方式建立應用程式定義域。  
  
 [操作說明：卸載應用程式定義域](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 描述如何以程式設計方式卸載應用程式定義域。  
  
 [操作說明：設定應用程式定義域](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 提供設定應用程式定義域的簡介。  
  
 [從應用程式定義域擷取安裝資訊](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 說明如何從應用程式定義域擷取安裝資訊。  
  
 [如何：將組件載入應用程式定義域](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 說明如何將組件載入應用程式定義域。  
  
 [操作說明：從組件中取得類型和成員資訊](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 說明如何擷取組件的相關資訊。  
  
 [陰影複製組件](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 說明陰影複製如何在使用組件時更新組件，以及如何設定陰影複製。  
  
 [操作說明：接收第一個可能發生的例外狀況通知](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 說明您如何在 Common Language Runtime 開始搜尋例外狀況處理常式之前，收到已擲回例外狀況的通知。  
  
 [解析組件載入](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 提供使用 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件解析組件載入失敗的指引。  
  
## <a name="reference"></a>參考資料  
 <xref:System.AppDomain>  
 代表應用程式定義域。 提供建立及控制應用程式定義域的方法。  
  
## <a name="related-sections"></a>相關章節  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供組件執行函式的概觀。  
  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 描述如何建立和簽署組件，以及如何設定組件屬性。  
  
 [發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 描述如何建立動態組件。  
  
 [應用程式定義域](../../../docs/framework/app-domains/application-domains.md)  
 提供應用程式定義域的概觀。  
  
 [反映概觀](../../../docs/framework/reflection-and-codedom/reflection.md)  
 描述如何使用「反映」類別，以取得組件的相關資訊。

