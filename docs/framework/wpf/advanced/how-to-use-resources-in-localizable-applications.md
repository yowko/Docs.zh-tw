---
title: HOW TO：在可當地語系化的應用程式中使用資源
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376153"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>HOW TO：在可當地語系化的應用程式中使用資源
當地語系化表示適應[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]不同文化特性。 若要執行這項操作，必須翻譯標題、說明文字、清單方塊項目等文字。 為了簡化翻譯過程，會將要翻譯的項目收集到資源檔中。 請參閱[將應用程式當地語系化](how-to-localize-an-application.md)如需如何建立當地語系化的資源檔的詳細資訊。 若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式當地語系化，開發人員建置成資源組件的所有可當地語系化的資源。 資源組件已當地語系化成不同的語言和程式碼後置使用資源管理[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]載入。 其中一個所需的檔案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是專案檔 (.proj)。 專案檔案應該包含您在應用程式中使用的所有資源。 下列程式碼範例會顯示這點。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 若要在您的應用程式中使用資源，您具現化<xref:System.Resources.ResourceManager>並載入您想要使用的資源。 以下示範如何執行這項操作。  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
