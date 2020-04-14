---
title: 如何透過本地化異常訊息建立使用者定義的例外
description: 瞭解如何使用本地化異常訊息建立使用者定義的例外
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243345"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>如何透過本地化異常訊息建立使用者定義的例外

在本文中,您將學習如何使用附屬程式集創建從基<xref:System.Exception>類繼承的使用者定義的異常,並帶有本地化的異常消息。

## <a name="create-custom-exceptions"></a>建立自訂異常

.NET 包含許多可以使用的不同異常。 但是,在某些情況下,當它們都無法滿足您的需求時,您可以創建自己的自定義異常。

假設您要建立`StudentNotFoundException`一`StudentName`個 包含屬性。
要建立自定義異常,請按照以下步驟操作:

1. 建立從 繼承<xref:System.Exception>的 可序列化類。 類別名稱應以「異常」結尾:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. 新增預設建構函數:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. 定義任何其他屬性與建構函數:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a>建立本地端的例外訊息

您已經建立了自訂異常,並且可以使用如下代碼將其扔到任何位置:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

上一行的問題是,`"The student cannot be found."`這只是一個常量字串。 在本地化應用程式中,您希望根據使用者區域性使用不同的消息。
[衛星元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)是做到這一點的好方法。 附屬程式集是包含特定語言資源的 .dll。 當您在執行時請求特定資源時,CLR 會根據使用者區域性找到該資源。 如果未找到該區域性的附屬程式集,則使用預設區域性的資源。

要創建當地化的異常消息,

1. 建立名為 *「資源」* 的新資料夾以儲存資源檔。
1. 向其添加新資源檔。 要在 Visual Studio 中執行此操作,請右鍵單擊**解決方案資源管理器****Add** > 中的資料夾 ,然後選擇「**添加新項目** > **資源檔**」 。 命名檔案*例外訊息.resx*. 。 這是預設資源檔。
1. 為異常消息添加名稱/值對,如下圖所示:

   ![新增資源到預設區域性](media/add-resources-to-default-culture.jpg)

1. 為法語添加新的資源檔。 將*將命名為 ExceptionMessages.fr-FR.resx*。
1. 再次為異常訊息添加名稱/值對,但使用法語值:

   ![將資源加入 fr-FR 區域性](media/add-resources-to-fr-culture.jpg)

1. 生成專案後,生成輸出資料夾應包含帶 *.dll*檔的*fr-FR*資料夾,該檔是附屬程式集。
1. 使用如下代碼引發異常:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > `TestProject`如果項目名稱稱為,並且資源檔*ExceptionMessages.resx*駐留在專案的 *「資源」* 資料夾中,則資源檔案的完全限定名稱為`TestProject.Resources.ExceptionMessages`。

## <a name="see-also"></a>另請參閱

- [如何建立使用者定義的例外](how-to-create-user-defined-exceptions.md)
- [建立桌面應用程式的附屬組件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# 參考)](../../csharp/language-reference/keywords/base.md)
- [this (C# 參考)](../../csharp/language-reference/keywords/this.md)
