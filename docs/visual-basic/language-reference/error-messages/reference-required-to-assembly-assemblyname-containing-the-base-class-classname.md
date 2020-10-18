---
title: 需要組件 '<assemblyname>' (包含基底類別 '<classname>') 的參考
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: d2fb3498219dfe3318ec418ede250de818874ba9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162332"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a>BC30007：需要元件 ' ' （ \<assemblyname> 包含基類 ' '）的 \<classname> 參考

需要元件 ' ' （ \<assemblyname> 包含基類 ' '）的參考 \<classname> 。 請在專案中加入一個參考。

 此類別是在專案中未直接參考的動態連結程式庫 (DLL) 或組件中所定義。 Visual Basic 編譯器需要參考，以避免在多個 DLL 或元件中定義類別的情況下不清楚。

 **錯誤 ID︰** BC30007

## <a name="to-correct-this-error"></a>更正這個錯誤

- 在您的專案參考中包含未參考之 DLL 或組件的名稱。

## <a name="see-also"></a>另請參閱

- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
