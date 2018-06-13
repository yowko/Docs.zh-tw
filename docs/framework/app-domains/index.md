---
title: 使用應用程式定義域和組件設計程式
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742428"
---
# <a name="programming-with-application-domains-and-assemblies"></a>使用應用程式定義域和組件設計程式
Microsoft Internet Explorer、ASP.NET 和 Windows 殼層這類主機會在執行 .NET Framework 應用程式時將通用語言執行平台載入至處理序、在該處理序中建立[應用程式定義域](../../../docs/framework/app-domains/application-domains.md)，然後在該應用程式定義域中載入並執行使用者程式碼。 在大部分情況下，您不必操心如何建立應用程式定義域並載入組件，因為執行階段主機會執行這些工作。  
  
 不過，如果您要建立將裝載通用語言執行平台的應用程式、建立您想要以程式設計方式卸載的工具或程式碼，或建立可即時卸載並重新載入的隨插即用元件，您就要建立您自己的應用程式定義域。 即使您沒有建立執行階段主機，本節仍會提供如何使用應用程式定義域，以及使用在這些應用程式定義域中載入之組件的重要資訊。  
  
## <a name="in-this-section"></a>本節內容  
 [應用程式定義域和組件操作說明主題](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 提供使用應用程式定義域和組件設計程式之概念文件中所有操作說明主題的連結。  
  
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)  
 提供建立、設定及使用應用程式定義域的範例。  
  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 描述如何建立和簽署組件，以及如何設定組件屬性。  
  
## <a name="related-sections"></a>相關章節  
 [發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 描述如何建立動態組件。  
  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供組件的概觀。  
  
 [應用程式定義域](../../../docs/framework/app-domains/application-domains.md)  
 提供應用程式定義域的概觀。  
  
 [反映概觀](../../../docs/framework/reflection-and-codedom/reflection.md)  
 描述如何使用「反映」類別，以取得組件的相關資訊。
