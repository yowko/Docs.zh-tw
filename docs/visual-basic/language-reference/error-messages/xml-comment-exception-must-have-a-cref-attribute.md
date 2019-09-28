---
title: XML 註解例外狀況必須有 'cref' 屬性
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592032"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="a08cd-102">XML 註解例外狀況必須有 'cref' 屬性</span><span class="sxs-lookup"><span data-stu-id="a08cd-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="a08cd-103">@No__t 0exception > 標記會提供一種方式，記載方法所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a08cd-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="a08cd-104">必要的 `cref` 屬性會指定檔產生器所檢查的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="a08cd-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="a08cd-105">如果成員存在，則會轉譯為檔檔中的標準專案名稱。</span><span class="sxs-lookup"><span data-stu-id="a08cd-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="a08cd-106">**錯誤識別碼：** BC42319</span><span class="sxs-lookup"><span data-stu-id="a08cd-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a08cd-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a08cd-107">To correct this error</span></span>  
  
- <span data-ttu-id="a08cd-108">將 `cref` 屬性新增至例外狀況，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a08cd-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    <span data-ttu-id="a08cd-109">Xml</span><span class="sxs-lookup"><span data-stu-id="a08cd-109">xml</span></span>  
    <span data-ttu-id="a08cd-110">' ' '<exception cref="member">描述</exception></span><span class="sxs-lookup"><span data-stu-id="a08cd-110">'''<exception cref="member">description</exception></span></span>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
