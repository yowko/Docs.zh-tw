---
title: 如何通過當地語系化的異常消息創建使用者定義的異常
description: 瞭解如何使用當地語系化的異常消息創建使用者定義的異常
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160179"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>如何通過當地語系化的異常消息創建使用者定義的異常

在本文中，您將學習如何使用附屬程式集創建從基<xref:System.Exception>類繼承的使用者定義的異常，並帶有當地語系化的異常消息。

## <a name="create-custom-exceptions"></a>創建自訂異常

.NET 包含許多可以使用的不同異常。 但是，在某些情況下，當它們都無法滿足您的需求時，您可以創建自己的自訂異常。

假設您要創建`StudentNotFoundException`一個`StudentName`包含屬性。
要創建自訂異常，請按照以下步驟操作：

1. 創建從 繼承的<xref:System.Exception>可序列化類。 類名稱應以"異常"結尾：

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

1. 添加預設建構函式：

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

1. 定義任何其他屬性和建構函式：

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

## <a name="create-localized-exception-messages"></a>創建當地語系化的異常消息

您已經創建了自訂異常，並且可以使用如下代碼將其扔到任何位置：

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

上一行的問題是，`"The student cannot be found."`這只是一個常量字串。 在當地語系化應用程式中，您希望根據使用者區域性使用不同的消息。
[衛星元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)是做到這一點的好方法。 附屬程式集是包含特定語言資源的 .dll。 當您在運行時請求特定資源時，CLR 會根據使用者區域性找到該資源。 如果未找到該區域性的附屬程式集，則使用預設區域性的資源。

要創建當地語系化的異常消息，

1. 創建名為 *"資源"* 的新資料夾以保存資源檔。
1. 向其添加新資源檔。 要在 Visual Studio 中執行此操作，請按右鍵**解決方案資源管理器**中的資料夾**Add** > ，然後選擇"**添加新專案** > **資源檔**"。 命名檔*例外消息.resx*. 。 這是預設資源檔。
1. 為異常消息添加名稱/值對，如下圖所示：

   ![將資源添加到預設區域性](media/add-resources-to-default-culture.jpg)

1. 為法語添加新的資源檔。 將其命名為*ExceptionMessages.fr-FR.resx*。
1. 再次為異常消息添加名稱/值對，但使用法語值：

   ![將資源添加到 fr-FR 區域性](media/add-resources-to-fr-culture.jpg)

1. 生成專案後，生成輸出檔案夾應包含帶 *.dll*檔的*fr-FR*資料夾，該檔是附屬程式集。
1. 使用如下代碼引發異常：

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > `TestProject`如果專案名稱為，並且資源檔*ExceptionMessages.resx*駐留在專案的 *"資源"* 資料夾中，則資源檔的完全限定名稱為`TestProject.Resources.ExceptionMessages`。

## <a name="see-also"></a>另請參閱

- [如何創建使用者定義的異常](how-to-create-user-defined-exceptions.md)
- [建立桌面應用程式的附屬組件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# 參考)](../../csharp/language-reference/keywords/base.md)
- [this (C# 參考)](../../csharp/language-reference/keywords/this.md)
