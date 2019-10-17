---
title: 如何：在 XAML 中使用特殊字元
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 27f2b18593d075b54eb8c3351bbb84415700cfd4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395796"
---
# <a name="how-to-use-special-characters-in-xaml"></a>如何：在 XAML 中使用特殊字元
在 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 中建立的標記檔會自動以 Unicode UTF-8 檔案格式儲存，這表示大部分的特殊字元（例如重音標記）都會正確編碼。 不過，有一組常用的特殊字元則採用不同的處理方式。 這些特殊字元會遵循 [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 標準以進行編碼。  
  
 下表顯示這組特殊字元的編碼語法：  
  
|字元|語法|描述|  
|---------------|------------|-----------------|  
|<|`&lt;`|小於符號。|  
|>|`&gt;`|大於符號。|  
|&|`&amp;`|& 符號。|  
|"|`&quot;`|雙引號。|  
  
> [!NOTE]
> 如果您使用文字編輯器（例如 Windows 記事本）來建立標記檔案，就必須以 Unicode UTF-8 檔案格式儲存檔案，才能保留任何編碼的特殊字元。  
  
 下列範例示範如何在建立標記時，於文字中使用特殊字元。  
  
## <a name="example"></a>範例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
