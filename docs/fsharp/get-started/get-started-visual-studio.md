---
title: "要开始使用 Visual Studio 中的 F #"
description: "了解如何使用 Visual Studio 中使用 F #。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 944bbbba6a26634ace269d86cbbdde9ef9de7bcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="bf486-104">要开始使用 Visual Studio 中的 F #</span><span class="sxs-lookup"><span data-stu-id="bf486-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="bf486-105">在 Visual Studio IDE 中支持 F # 和 Visual F # 工具。</span><span class="sxs-lookup"><span data-stu-id="bf486-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="bf486-106">若要开始，你应[下载 Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs)，如果你尚未。</span><span class="sxs-lookup"><span data-stu-id="bf486-106">To begin, you should [download Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), if you haven't already.</span></span>  <span data-ttu-id="bf486-107">本文章将使用 Visual Studio 2017 Community Edition，但你可以使用 F # 与所选的版本。</span><span class="sxs-lookup"><span data-stu-id="bf486-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="bf486-108">正在安装 F #</span><span class="sxs-lookup"><span data-stu-id="bf486-108">Installing F#</span></span> #

<span data-ttu-id="bf486-109">如果您正在第一次下载 Visual Studio，它将首先安装 Visual Studio 安装程序。</span><span class="sxs-lookup"><span data-stu-id="bf486-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="bf486-110">从安装程序安装任何版本的 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="bf486-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="bf486-111">如果你已安装，请单击**修改**。</span><span class="sxs-lookup"><span data-stu-id="bf486-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="bf486-112">接下来，你将看到一份工作负荷。</span><span class="sxs-lookup"><span data-stu-id="bf486-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="bf486-113">你可以安装 F # 通过任何以下工作负荷：</span><span class="sxs-lookup"><span data-stu-id="bf486-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="bf486-114">工作负荷</span><span class="sxs-lookup"><span data-stu-id="bf486-114">Workload</span></span>|<span data-ttu-id="bf486-115">操作</span><span class="sxs-lookup"><span data-stu-id="bf486-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="bf486-116">.NET Core 跨平台开发</span><span class="sxs-lookup"><span data-stu-id="bf486-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="bf486-117">默认情况下不安装任何操作-F #</span><span class="sxs-lookup"><span data-stu-id="bf486-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="bf486-118">ASP.NET 和 Web 开发</span><span class="sxs-lookup"><span data-stu-id="bf486-118">ASP.NET and web development</span></span> | <span data-ttu-id="bf486-119">默认情况下不安装任何操作-F #</span><span class="sxs-lookup"><span data-stu-id="bf486-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="bf486-120">Azure 开发</span><span class="sxs-lookup"><span data-stu-id="bf486-120">Azure development</span></span> | <span data-ttu-id="bf486-121">默认情况下不安装任何操作-F #</span><span class="sxs-lookup"><span data-stu-id="bf486-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="bf486-122">使用 .NET 的移动开发</span><span class="sxs-lookup"><span data-stu-id="bf486-122">Mobile development with .NET</span></span> | <span data-ttu-id="bf486-123">默认情况下不安装任何操作-F #</span><span class="sxs-lookup"><span data-stu-id="bf486-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="bf486-124">数据科学和分析应用程序</span><span class="sxs-lookup"><span data-stu-id="bf486-124">Data science and analytical applications</span></span> | <span data-ttu-id="bf486-125">默认情况下不安装任何操作-F #</span><span class="sxs-lookup"><span data-stu-id="bf486-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="bf486-126">.NET 桌面开发</span><span class="sxs-lookup"><span data-stu-id="bf486-126">.NET desktop development</span></span> | <span data-ttu-id="bf486-127">选择**F # 桌面语言支持**从右侧</span><span class="sxs-lookup"><span data-stu-id="bf486-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="bf486-128">数据存储和处理</span><span class="sxs-lookup"><span data-stu-id="bf486-128">Data storage and processing</span></span> | <span data-ttu-id="bf486-129">选择**F # 桌面语言支持**从右侧</span><span class="sxs-lookup"><span data-stu-id="bf486-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="bf486-130">接下来，单击**修改**的右下方中。</span><span class="sxs-lookup"><span data-stu-id="bf486-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="bf486-131">这将安装您选择的所有内容。</span><span class="sxs-lookup"><span data-stu-id="bf486-131">This will install everything you have selected.</span></span>  <span data-ttu-id="bf486-132">随后可打开 Visual Studio 2017 使用 F # 语言支持通过单击**启动**。</span><span class="sxs-lookup"><span data-stu-id="bf486-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="bf486-133">创建一个控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="bf486-133">Creating a console application</span></span>

<span data-ttu-id="bf486-134">Visual Studio 中最基本的项目之一是控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf486-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="bf486-135">以下是使用方法。</span><span class="sxs-lookup"><span data-stu-id="bf486-135">Here's how to do it.</span></span>  <span data-ttu-id="bf486-136">打开 Visual Studio 后：</span><span class="sxs-lookup"><span data-stu-id="bf486-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="bf486-137">上**文件**菜单上，指向**新建**，然后选择**项目**。</span><span class="sxs-lookup"><span data-stu-id="bf486-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="bf486-138">在新建项目对话框中下,**模板**，你应该会看到**Visual F #**。</span><span class="sxs-lookup"><span data-stu-id="bf486-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="bf486-139">选择此选项可显示 F # 模板。</span><span class="sxs-lookup"><span data-stu-id="bf486-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="bf486-140">选择**.NET 核心控制台应用程序**或**控制台应用程序**。</span><span class="sxs-lookup"><span data-stu-id="bf486-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="bf486-141">选择**好**按钮以创建 F # 项目 ！</span><span class="sxs-lookup"><span data-stu-id="bf486-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="bf486-142">你现在应该看到解决方案资源管理器中的 F # 项目。</span><span class="sxs-lookup"><span data-stu-id="bf486-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="bf486-143">编写代码</span><span class="sxs-lookup"><span data-stu-id="bf486-143">Writing your code</span></span>

<span data-ttu-id="bf486-144">让我们开始吧通过首先编写一些代码。</span><span class="sxs-lookup"><span data-stu-id="bf486-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="bf486-145">请确保`Program.fs`文件已打开，，然后将其内容替换为以下：</span><span class="sxs-lookup"><span data-stu-id="bf486-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="bf486-146">在前面的代码示例，函数`square`具有已定义接受名为输入`x`和乘以它本身。</span><span class="sxs-lookup"><span data-stu-id="bf486-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="bf486-147">因为 F # 使用[类型推理](../language-reference/type-inference.md)的一种`x`不需要指定。</span><span class="sxs-lookup"><span data-stu-id="bf486-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="bf486-148">F # 编译器了解有效，乘法的类型，将分配到的类型`x`具体取决于`square`调用。</span><span class="sxs-lookup"><span data-stu-id="bf486-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="bf486-149">如果将鼠标悬停在`square`，则应查看以下信息：</span><span class="sxs-lookup"><span data-stu-id="bf486-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="bf486-150">这就是所谓的函数的类型签名。</span><span class="sxs-lookup"><span data-stu-id="bf486-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="bf486-151">它可以读取如下:"平方形是一个函数，将名为一个整数 x，并生成一个整数"。</span><span class="sxs-lookup"><span data-stu-id="bf486-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="bf486-152">请注意，编译器会为提供`square``int`类型现在-这是因为乘法不是泛型跨*所有*类型，但而是泛型类型的封闭集。</span><span class="sxs-lookup"><span data-stu-id="bf486-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="bf486-153">F # 编译器选取`int`在这点，但它将调整类型签名如果调用`square`替换为其他输入类型，如`float`。</span><span class="sxs-lookup"><span data-stu-id="bf486-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="bf486-154">另一个函数， `main`，定义，这用修饰`EntryPoint`属性指示该程序执行的 F # 编译器应从那里开始。</span><span class="sxs-lookup"><span data-stu-id="bf486-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="bf486-155">它遵循相同的约定与其他[C 样式编程语言](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)，其中可以对此函数，传递命令行自变量，则返回的整数代码 (通常`0`)。</span><span class="sxs-lookup"><span data-stu-id="bf486-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="bf486-156">我们调用此函数在`square`用参数的函数`12`。</span><span class="sxs-lookup"><span data-stu-id="bf486-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="bf486-157">F # 编译器然后将分配的一种`square`要`int -> int`(即，采用的函数`int`并生成`int`)。</span><span class="sxs-lookup"><span data-stu-id="bf486-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="bf486-158">调用`printfn`是格式化的打印函数使用类似于 C 样式编程语言，它们分别对应于格式字符串中指定的参数的格式字符串，然后输出结果和新行。</span><span class="sxs-lookup"><span data-stu-id="bf486-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="bf486-159">运行代码</span><span class="sxs-lookup"><span data-stu-id="bf486-159">Running your code</span></span>

<span data-ttu-id="bf486-160">你可以运行该代码并查看结果，通过按**ctrl-f5**。</span><span class="sxs-lookup"><span data-stu-id="bf486-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="bf486-161">这将运行程序而不进行调试，并允许你以查看结果。</span><span class="sxs-lookup"><span data-stu-id="bf486-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="bf486-162">或者，你可以选择**调试**顶级菜单项在 Visual Studio 中，然后选择**启动但不调试**。</span><span class="sxs-lookup"><span data-stu-id="bf486-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="bf486-163">你现在应看到以下输出到控制台窗口的 Visual Studio 弹出：</span><span class="sxs-lookup"><span data-stu-id="bf486-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="bf486-164">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="bf486-164">Congratulations!</span></span>  <span data-ttu-id="bf486-165">你在 Visual Studio 中创建第一个 F # 项目、 编写 F # 函数打印调用该函数的结果并运行项目以查看部分结果。</span><span class="sxs-lookup"><span data-stu-id="bf486-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="bf486-166">使用 F # Interactive</span><span class="sxs-lookup"><span data-stu-id="bf486-166">Using F# Interactive</span></span>

<span data-ttu-id="bf486-167">最佳功能的 Visual F # 工具在 Visual Studio 中的一个是 F # 交互式窗口。</span><span class="sxs-lookup"><span data-stu-id="bf486-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="bf486-168">它允许您通过代码发送到的进程可以在此调用该代码，并以交互方式查看结果。</span><span class="sxs-lookup"><span data-stu-id="bf486-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="bf486-169">若要开始使用它，突出显示`square`你代码中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="bf486-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="bf486-170">接下来，保存**Alt**键，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="bf486-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="bf486-171">这在 F # 交互式窗口中执行代码。</span><span class="sxs-lookup"><span data-stu-id="bf486-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="bf486-172">你应看到 F # 交互式窗口中它的以下一起显示：</span><span class="sxs-lookup"><span data-stu-id="bf486-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="bf486-173">下面的示例演示的相同函数签名`square`函数，你此前看到当悬停在该函数。</span><span class="sxs-lookup"><span data-stu-id="bf486-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="bf486-174">因为`square`是现在在 F # Interactive 的过程中定义，则可以调用它时使用不同的值：</span><span class="sxs-lookup"><span data-stu-id="bf486-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="bf486-175">此程序执行的函数，请将结果绑定到的新名称`it`，并显示类型和值`it`。</span><span class="sxs-lookup"><span data-stu-id="bf486-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="bf486-176">请注意，必须终止与每个行`;;`。</span><span class="sxs-lookup"><span data-stu-id="bf486-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="bf486-177">这是如何 F # Interactive 知道函数调用完成时。</span><span class="sxs-lookup"><span data-stu-id="bf486-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="bf486-178">你还可以在 F # Interactive 中定义新的函数：</span><span class="sxs-lookup"><span data-stu-id="bf486-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="bf486-179">上述定义了一个新的函数， `isOdd`，此方法采用`int`和检查，以查看它是否是奇数 ！</span><span class="sxs-lookup"><span data-stu-id="bf486-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="bf486-180">你可以调用此函数可看到它使用不同的输入返回。</span><span class="sxs-lookup"><span data-stu-id="bf486-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="bf486-181">你可以调用函数调用中的函数：</span><span class="sxs-lookup"><span data-stu-id="bf486-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="bf486-182">你还可以使用[管道进运算符](../language-reference/symbol-and-operator-reference/index.md)管线值传输到两个函数：</span><span class="sxs-lookup"><span data-stu-id="bf486-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="bf486-183">管道进运算符，和的详细信息，详见更高版本的教程。</span><span class="sxs-lookup"><span data-stu-id="bf486-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="bf486-184">这是仅一下如何使用 F # Interactive。</span><span class="sxs-lookup"><span data-stu-id="bf486-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="bf486-185">若要了解详细信息，请查看[使用 F # 进行交互式编程](../tutorials/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bf486-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bf486-186">后续步骤</span><span class="sxs-lookup"><span data-stu-id="bf486-186">Next steps</span></span>

<span data-ttu-id="bf486-187">如果你尚未这样做，请查看[教程的 F #](../tour.md)，其中介绍了一些 F # 语言的核心功能。</span><span class="sxs-lookup"><span data-stu-id="bf486-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="bf486-188">它将为你提供一些 F # 的功能的概述，并提供充足的代码示例，你可以将复制到 Visual Studio 并运行。</span><span class="sxs-lookup"><span data-stu-id="bf486-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="bf486-189">此外还有一些有用的外部资源，你可以使用，在演示了[F # 指南](../index.md)。</span><span class="sxs-lookup"><span data-stu-id="bf486-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bf486-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf486-190">See also</span></span>
 [<span data-ttu-id="bf486-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="bf486-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="bf486-192">F# 教程</span><span class="sxs-lookup"><span data-stu-id="bf486-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="bf486-193">F # 语言参考</span><span class="sxs-lookup"><span data-stu-id="bf486-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="bf486-194">类型推理</span><span class="sxs-lookup"><span data-stu-id="bf486-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="bf486-195">符号和运算符参考</span><span class="sxs-lookup"><span data-stu-id="bf486-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  