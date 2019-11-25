---
title: 屬性和變數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341214"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic 中屬性和變數的差別
Variables and properties both represent values that you can access. However, there are differences in storage and implementation.  
  
## <a name="variables"></a>變數  
 A *variable* corresponds directly to a memory location. You define a variable with a single declaration statement. A variable can be a *local variable*, defined inside a procedure and available only within that procedure, or it can be a *member variable*, defined in a module, class, or structure but not inside any procedure. A member variable is also called a *field*.  
  
## <a name="properties"></a>內容  
 A *property* is a data element defined on a module, class, or structure. You define a property with a code block between the `Property` and `End Property` statements. The code block contains a `Get` procedure, a `Set` procedure, or both. These procedures are called *property procedures* or *property accessors*. In addition to retrieving or storing the property's value, they can also perform custom actions, such as updating an access counter.  
  
## <a name="differences"></a>Differences  
 The following table shows some important differences between variables and properties.  
  
|Point of difference|變數|屬性|  
|-------------------------|--------------|--------------|  
|宣告|Single declaration statement|Series of statements in a code block|  
|實作|Single storage location|Executable code (property procedures)|  
|存放裝置|Directly associated with variable's value|Typically has internal storage not available outside the property's containing class or module<br /><br /> Property's value might or might not exist as a stored element <sup>1</sup>|  
|Executable code|None|Must have at least one procedure|  
|Read and write access|Read/write or read-only|Read/write, read-only, or write-only|  
|Custom actions (in addition to accepting or returning value)|Not possible|Can be performed as part of setting or retrieving property value|  
  
 <sup>1</sup> Unlike a variable, the value of a property might not correspond directly to a single item of storage. The storage might be split into pieces for convenience or security, or the value might be stored in an encrypted form. In these cases the `Get` procedure would assemble the pieces or decrypt the stored value, and the `Set` procedure would encrypt the new value or split it into the constituent storage. A property value might be ephemeral, like time of day, in which case the `Get` procedure would calculate it on the fly each time you access the property.  
  
## <a name="see-also"></a>請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
