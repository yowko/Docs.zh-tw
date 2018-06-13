---
title: 如何：在可當地語系化的應用程式中使用資源
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 82a24feb4008b6cfd7c1751c6449c0d8515ffe87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544699"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>如何：在可當地語系化的應用程式中使用資源
當地語系化表示調整[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]至不同的文化特性。 若要執行這項操作，必須翻譯標題、說明文字、清單方塊項目等文字。 為了簡化翻譯過程，會將要翻譯的項目收集到資源檔中。 請參閱[當地語系化應用程式](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)如需如何建立當地語系化的資源檔的資訊。 若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式當地語系化，開發人員必須建置成資源組件的所有可當地語系化的資源。 資源組件已當地語系化成不同的語言和程式碼後置會使用資源管理[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]載入。 其中一個所需的檔案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是專案檔 (.proj)。 專案檔案應該包含您在應用程式中使用的所有資源。 下列程式碼範例會顯示這點。  
  
## <a name="example"></a>範例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 在您的應用程式中使用的資源，您具現化<xref:System.Resources.ResourceManager>和載入您想要使用的資源。 以下示範如何執行這項操作。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
