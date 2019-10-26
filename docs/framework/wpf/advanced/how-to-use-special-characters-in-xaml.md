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
ms.openlocfilehash: 713428adc2e1576d1b95984b492fe84c042c0a09
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919635"
---
# <a name="how-to-use-special-characters-in-xaml"></a>如何：在 XAML 中使用特殊字元
在 Visual Studio 中建立的標記檔會自動以 Unicode UTF-8 檔案格式儲存，這表示大部分的特殊字元（例如重音標記）都會正確編碼。 不過，有一組常用的特殊字元則採用不同的處理方式。 這些特殊字元遵循全球資訊網協會（W3C） [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 標準編碼。  
  
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
