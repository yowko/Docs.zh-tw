---
title: "全球化和當地語系化 .NET Framework 應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: 42
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: d6313cea51b98b3b19363f3c465e5adf241ab3d4
ms.lasthandoff: 04/08/2017

---
# <a name="globalizing-and-localizing-net-framework-applications"></a>全球化和當地語系化 .NET Framework 應用程式
開發[世界通用的應用程式](http://msdn.microsoft.com/goglobal/bb978433.aspx)，包括可以當地語系化為一種或多種語言的應用程式，這項開發工作包含三個步驟：全球化、可當地語系化檢閱，以及當地語系化。  
  
 [全球化](../../../docs/standard/globalization-localization/globalization.md)  
 這個步驟包含設計和撰寫文化特性中性和語言中性的應用程式程式碼，且該應用程式支援當地語系化使用者介面和所有使用者的區域資料。 這個步驟包含不是根據文化特性假設做出的設計和開發決策。 即使全球化的應用程式並未當地語系化，但是它的設計和撰寫方式讓後續能夠相對方便地進行一種或多種語言的當地語系化。  
  
 [可當地語系化檢閱](../../../docs/standard/globalization-localization/localizability-review.md)  
 這個步驟包含檢閱應用程式的程式碼和設計，確保它可以輕鬆地當地語系化並識別當地語系化時可能發生的阻礙，以及確認應用程式的可執行碼與其資源分開。 如果全球化階段有效，則當地語系化能力檢閱將確認全球化期間所選擇的設計和編碼。 當地語系化能力階段也可能會找出任何其餘的問題，如此應用程式的原始程式碼就不需要在當地語系化階段進行修改。  
  
 [當地語系化](../../../docs/standard/globalization-localization/localization.md)  
 這個步驟包含自訂特定文化特性或地區的應用程式。 如果已正確執行全球化和當地語系化能力的步驟，則當地語系化的主要工作就是轉譯使用者介面。  
  
 依照下列三個步驟執行可提供兩項優點：  
  
-   您不需要重新設計用於支援單一文化特性 (例如英文 (美國)) 的應用程式，即可支援其他文化特性。  
  
-   可產生更穩定且較少 Bug 的當地語系化應用程式。  
  
 .NET Framework 提供各種開發世界通用及當地語系化應用程式的支援。 特別是，.NET Framework 類別庫中的許多類型成員會傳回反映目前使用者文化特性或特定文化特性慣例的值，藉以協助全球化。 此外，.NET Framework 還支援附屬組件，可簡化當地語系化應用程式的程序。  
  
 如需詳細資訊，請參閱[全球化開發人員中心 (英文)](http://go.microsoft.com/fwlink/?LinkId=235015)。  
  
## <a name="in-this-section"></a>本章節內容  
 [全球化](../../../docs/standard/globalization-localization/globalization.md)  
 討論建立世界通用應用程式的第一個階段，包括設計和撰寫文化特性中性和語言中性之應用程式的程式碼。  
  
 [可當地語系化檢閱](../../../docs/standard/globalization-localization/localizability-review.md)  
 討論建立當地語系化應用程式的第二個階段，包括識別當地語系化過程中可能遭遇到的阻礙。  
  
 [當地語系化](../../../docs/standard/globalization-localization/localization.md)  
 討論建立當地語系化應用程式的最後一個階段，包括自訂特定區域或文化特性的應用程式使用者介面。  
  
 [不區分文化特性的字串之作業](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 說明如何使用預設為區分文化特性的 .NET Framework 方法和類別來取得不區分文化特性的結果。  
  
 [開發世界性的應用程式的最佳做法](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 說明進行全球化、當地語系化和開發世界性的 ASP.NET 的最佳實施方針。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Globalization?displayProperty=fullName> 命名空間  
 包含類別，定義與文化特性相關的資訊，包括語言、國家/地區、使用中的日曆、日期、貨幣和數字的格式模式，以及字串的排序順序。  
  
 <xref:System.Resources> 命名空間  
 提供建立、管理和使用資源的類別。  
  
 <xref:System.Text> 命名空間  
 包含表示 ASCII、ANSI、Unicode 和其他字元編碼方式的類別。  
  
 [Resgen.exe (資源檔產生器)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 描述如何使用 Resgen.exe 來轉換 .txt 檔案和 XML 資源格式 (.resx) 檔案到通用語言執行平台二進位資源檔。  
  
 [Winres.exe (Windows Forms 資源編輯器)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 描述如何使用 Winres.exe 將 Windows Form 表單當地語系化。
