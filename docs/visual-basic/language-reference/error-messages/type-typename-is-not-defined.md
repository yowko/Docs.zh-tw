---
title: 類型 '<typename>' 未定義
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 89e2d1d18b456c96f62d6b9ee1dd8dc9d41bf665
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386928"
---
# <a name="type-typename-is-not-defined"></a>類型 '\<typename>' 未定義
語句已參考尚未定義的類型。 您可以在宣告語句中定義類型 `Enum` ，例如、 `Structure` 、 `Class` 或 `Interface` 。  
  
 **錯誤識別碼：** BC30002  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請確定類型定義及其參考皆使用相同的拼寫。  
  
- 請確定類型定義可供參考存取。 例如，如果類型是在另一個模組中且已宣告 `Private` ，請將類型定義移至參考模組，或將其宣告 `Public` 。  
  
- 請確定您的專案中未重新定義類型的命名空間。 如果是，請使用 `Global` 關鍵字來完整限定型別名稱。 例如，如果專案定義名為的命名空間 `System` ，則 <xref:System.Object?displayProperty=nameWithType> 無法存取類型，除非它是以關鍵字完整限定的 `Global` ： `Global.System.Object` 。  
  
- 如果已定義類型，但未在 Visual Basic 中註冊其定義所在的物件程式庫或類型程式庫，請按一下 [**專案**] 功能表上的 [**加入參考**]，然後選取適當的物件程式庫或類型程式庫。  
  
- 請確定該類型位於屬於目標 .NET Framework 設定檔一部分的元件中。 如需詳細資訊，請參閱[針對 .NET Framework 目標錯誤進行疑難排解](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)
- [End 陳述式](../statements/enum-statement.md)
- [Structure 陳述式](../statements/structure-statement.md)
- [Class 陳述式](../statements/class-statement.md)
- [Interface 陳述式](../statements/interface-statement.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
