---
title: 已建立內嵌 Interop 組件 '<assembly1>' 的參考，因為該組件的間接參考來自組件 '<assembly2>'。
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 058aa4891d05147756290affd60ea5fb260c33ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262948"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>已建立內嵌 interop 組件參考 '\<assembly1 >' 因為該組件的間接參考來自組件'\<assembly2 >'
已建立內嵌 Interop 組件 '\<assembly1>' 的參考，因為該組件的間接參考來自組件 '\<assembly2>'。 請考慮變更其中任何一個組件上的 [內嵌 Interop 類型] 屬性。  
  
 您已新增組件 (assembly1) 的參考，該組件的 `Embed Interop Types` 屬性已設定為 `True`。 這會指示編譯器內嵌該組件中的 Interop 類型資訊。 不過，編譯器無法內嵌該組件中的 Interop 類型資訊，因為您所參考的另一個組件 (assembly2) 也在參考該組件 (assembly1)，而且其 `Embed Interop Types` 屬性已設定為 `False`。  
  
> [!NOTE]
>  將組件參考的 `Embed Interop Types` 屬性設定為 `True`，相當於使用命令列編譯器的 `/link` 選項。  
  
 **錯誤 ID:** BC40059  
  
### <a name="to-address-this-warning"></a>解決這個警告  
  
-   若要同時內嵌這兩個組件的 Interop 類型資訊，請將所有 assembly1 參考的 `Embed Interop Types` 屬性都設定為 `True`。  
  
-   若要移除警告，您可以將 assembly1 的 `Embed Interop Types` 屬性設定為 `False`。 在此情況下，主要 interop 組件 (PIA) 所提供的 interop 類型資訊。  
  
## <a name="see-also"></a>另請參閱
- [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [與 Unmanaged 程式碼互通](../../../framework/interop/index.md)
