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
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="15e0c-102">如何：在 XAML 中使用特殊字元</span><span class="sxs-lookup"><span data-stu-id="15e0c-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="15e0c-103">標記檔案中建立[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]自動儲存在[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]utf-8 的檔案格式，這表示大部分的特殊字元，例如重音符號會正確編碼。</span><span class="sxs-lookup"><span data-stu-id="15e0c-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="15e0c-104">不過，有一組常用的特殊字元則採用不同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="15e0c-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="15e0c-105">請遵循這些特殊字元[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]標準的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="15e0c-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="15e0c-106">下表顯示這組特殊字元的編碼語法：</span><span class="sxs-lookup"><span data-stu-id="15e0c-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="15e0c-107">字元</span><span class="sxs-lookup"><span data-stu-id="15e0c-107">Character</span></span>|<span data-ttu-id="15e0c-108">語法</span><span class="sxs-lookup"><span data-stu-id="15e0c-108">Syntax</span></span>|<span data-ttu-id="15e0c-109">描述</span><span class="sxs-lookup"><span data-stu-id="15e0c-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="15e0c-110">小於符號。</span><span class="sxs-lookup"><span data-stu-id="15e0c-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="15e0c-111">大於符號。</span><span class="sxs-lookup"><span data-stu-id="15e0c-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="15e0c-112">& 符號。</span><span class="sxs-lookup"><span data-stu-id="15e0c-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="15e0c-113">"</span><span class="sxs-lookup"><span data-stu-id="15e0c-113">"</span></span>|`"`|<span data-ttu-id="15e0c-114">雙引號。</span><span class="sxs-lookup"><span data-stu-id="15e0c-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="15e0c-115">如果您建立標記檔案，使用文字編輯器 中，例如[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]「 記事本 」，您必須儲存在檔案[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]utf-8 檔案格式，以維持任何編碼的特殊字元。</span><span class="sxs-lookup"><span data-stu-id="15e0c-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="15e0c-116">下列範例示範如何在建立標記時，於文字中使用特殊字元。</span><span class="sxs-lookup"><span data-stu-id="15e0c-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15e0c-117">範例</span><span class="sxs-lookup"><span data-stu-id="15e0c-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
