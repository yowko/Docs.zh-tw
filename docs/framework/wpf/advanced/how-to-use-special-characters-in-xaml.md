---
title: "如何：在 XAML 中使用特殊字元"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79df87d716224cb8681c1688d94fe56077452c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a>如何：在 XAML 中使用特殊字元
標記檔案中建立[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]自動儲存在[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]utf-8 的檔案格式，這表示大部分的特殊字元，例如重音符號會正確編碼。 不過，有一組常用的特殊字元則採用不同的處理方式。 請遵循這些特殊字元[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]標準的編碼方式。  
  
 下表顯示這組特殊字元的編碼語法：  
  
|字元|語法|描述|  
|---------------|------------|-----------------|  
|<|`<`|小於符號。|  
|>|`>`|大於符號。|  
|&|`&`|& 符號。|  
|"|`"`|雙引號。|  
  
> [!NOTE]
>  如果您建立標記檔案，使用文字編輯器 中，例如[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]「 記事本 」，您必須儲存在檔案[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]utf-8 檔案格式，以維持任何編碼的特殊字元。  
  
 下列範例示範如何在建立標記時，於文字中使用特殊字元。  
  
## <a name="example"></a>範例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
