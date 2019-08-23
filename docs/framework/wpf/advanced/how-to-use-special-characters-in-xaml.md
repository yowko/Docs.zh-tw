---
title: HOW TO：在 XAML 中使用特殊字元
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918439"
---
# <a name="how-to-use-special-characters-in-xaml"></a>HOW TO：在 XAML 中使用特殊字元
在中[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]建立的標記檔案會自動儲存[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]為 utf-8 檔案格式, 這表示大部分的特殊字元 (例如重音標記) 都會正確編碼。 不過，有一組常用的特殊字元則採用不同的處理方式。 這些特殊字元會遵循[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)]標準進行編碼。  
  
 下表顯示這組特殊字元的編碼語法：  
  
|字元|語法|說明|  
|---------------|------------|-----------------|  
|<|`&lt;`|小於符號。|  
|>|`&gt;`|大於符號。|  
|&|`&amp;`|& 符號。|  
|"|`&quot;`|雙引號。|  
  
> [!NOTE]
> 如果您使用文字編輯器 (例如 Windows 記事本) 來建立標記檔案, 就必須以[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] utf-8 檔案格式儲存檔案, 才能保留任何編碼的特殊字元。  
  
 下列範例示範如何在建立標記時，於文字中使用特殊字元。  
  
## <a name="example"></a>範例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
