---
title: 晚期繫結程序解析; 可能發生執行階段錯誤
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397346"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>晚期繫結程序解析; 可能發生執行階段錯誤
已將物件指派給宣告為[Object 資料類型](../data-types/object-data-type.md)的變數。  
  
 當您將變數宣告為時 `Object` ，編譯器必須執行*晚期繫結*，這會在執行時間造成額外的作業。 它也可能會讓您的應用程式發生執行階段錯誤。 例如，如果您將指派 <xref:System.Windows.Forms.Form> 給變數， `Object` 然後嘗試存取 <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> 屬性，則執行時間會擲回， <xref:System.MemberAccessException> 因為類別不 <xref:System.Windows.Forms.Form> 會公開 `NameTable` 屬性。  
  
 如果您將變數宣告為特定類型，編譯器可以在編譯時期執行*早期繫結*。 這會改善效能、控制特定類型成員的存取權限，以及更好的程式碼可讀性。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC42017  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 可能的話，請將變數宣告為特定類型。  
  
## <a name="see-also"></a>另請參閱

- [早期和晚期繫結](../../programming-guide/language-features/early-late-binding/index.md)
- [物件變數宣告](../../programming-guide/language-features/variables/object-variable-declaration.md)
