---
title: "查询表达式 (F#)"
description: "了解有关 F # 编程语言中的 LINQ 查询表达式支持。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35df2d80-e6d2-4873-b2de-9b45b9e9e650
ms.openlocfilehash: 360733d81f049cd4356ecc47a27f97c3ec3a402a
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2017
---
# <a name="query-expressions"></a><span data-ttu-id="a4941-104">查询表达式</span><span class="sxs-lookup"><span data-stu-id="a4941-104">Query Expressions</span></span>

> [!NOTE]
<span data-ttu-id="a4941-105">本文中的 API 参考链接将转至 MSDN。</span><span class="sxs-lookup"><span data-stu-id="a4941-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a4941-106">Docs.microsoft.com API 参考尚未完成。</span><span class="sxs-lookup"><span data-stu-id="a4941-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a4941-107">查询表达式，可以查询数据源并将数据放入所需的形式。</span><span class="sxs-lookup"><span data-stu-id="a4941-107">Query expressions enable you to query a data source and put the data in a desired form.</span></span> <span data-ttu-id="a4941-108">查询表达式提供有关 F # 中的 LINQ 的支持。</span><span class="sxs-lookup"><span data-stu-id="a4941-108">Query expressions provide support for LINQ in F#.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4941-109">语法</span><span class="sxs-lookup"><span data-stu-id="a4941-109">Syntax</span></span>

```fsharp
query { expression }
```

## <a name="remarks"></a><span data-ttu-id="a4941-110">备注</span><span class="sxs-lookup"><span data-stu-id="a4941-110">Remarks</span></span>
<span data-ttu-id="a4941-111">查询表达式是一种类似于序列表达式的计算表达式。</span><span class="sxs-lookup"><span data-stu-id="a4941-111">Query expressions are a type of computation expression similar to sequence expressions.</span></span> <span data-ttu-id="a4941-112">就像通过提供代码中为序列表达式指定一个序列，将通过提供查询表达式中的代码中指定一组数据。</span><span class="sxs-lookup"><span data-stu-id="a4941-112">Just as you specify a sequence by providing code in a sequence expression, you specify a set of data by providing code in a query expression.</span></span> <span data-ttu-id="a4941-113">在序列表达式中，`yield`关键字标识作为生成的序列的一部分返回的数据。</span><span class="sxs-lookup"><span data-stu-id="a4941-113">In a sequence expression, the `yield` keyword identifies data to be returned as part of the resulting sequence.</span></span> <span data-ttu-id="a4941-114">在查询表达式中，`select`关键字执行相同的功能。</span><span class="sxs-lookup"><span data-stu-id="a4941-114">In query expressions, the `select` keyword performs the same function.</span></span> <span data-ttu-id="a4941-115">除了`select`关键字，F # 还支持大量的查询运算符，它非常类似的 SQL SELECT 语句的组成部分。</span><span class="sxs-lookup"><span data-stu-id="a4941-115">In addition to the `select` keyword, F# also supports a number of query operators that are much like the parts of a SQL SELECT statement.</span></span> <span data-ttu-id="a4941-116">下面是简单的查询表达式，以及连接到 Northwind OData 源的代码的示例。</span><span class="sxs-lookup"><span data-stu-id="a4941-116">Here is an example of a simple query expression, along with code that connects to the Northwind OData source.</span></span>

```fsharp
// Use the OData type provider to create types that can be used to access the Northwind database.
// Add References to FSharp.Data.TypeProviders and System.Data.Services.Client
open Microsoft.FSharp.Data.TypeProviders

type Northwind = ODataService<"http://services.odata.org/Northwind/Northwind.svc">
let db = Northwind.GetDataContext()

// A query expression.
let query1 =
    query {
        for customer in db.Customers do
            select customer
    }

// Print results
query1
|> Seq.iter (fun customer -> printfn "Company: %s Contact: %s" customer.CompanyName customer.ContactName)
```

<span data-ttu-id="a4941-117">在前面的代码示例中，查询表达式是在大括号中。</span><span class="sxs-lookup"><span data-stu-id="a4941-117">In the previous code example, the query expression is in curly braces.</span></span> <span data-ttu-id="a4941-118">表达式中的代码的含义是，在查询结果中的数据库中的 Customers 表中返回每个客户。</span><span class="sxs-lookup"><span data-stu-id="a4941-118">The meaning of the code in the expression is, return every customer in the Customers table in the database in the query results.</span></span> <span data-ttu-id="a4941-119">查询表达式返回的类型实现<xref:System.Linq.IQueryable%601>和<xref:System.Collections.Generic.IEnumerable%601>，因此，它们可循环使用[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)如示例所示。</span><span class="sxs-lookup"><span data-stu-id="a4941-119">Query expressions return a type that implements <xref:System.Linq.IQueryable%601> and <xref:System.Collections.Generic.IEnumerable%601>, and so they can be iterated using the [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) as the example shows.</span></span>

<span data-ttu-id="a4941-120">从生成器类生成每个计算表达式类型。</span><span class="sxs-lookup"><span data-stu-id="a4941-120">Every computation expression type is built from a builder class.</span></span> <span data-ttu-id="a4941-121">Query 计算表达式的生成器类是`QueryBuilder`。</span><span class="sxs-lookup"><span data-stu-id="a4941-121">The builder class for the query computation expression is `QueryBuilder`.</span></span> <span data-ttu-id="a4941-122">有关详细信息，请参阅[计算表达式](computation-expressions.md)和[Linq.QueryBuilder 类](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="a4941-122">For more information, see [Computation Expressions](computation-expressions.md) and [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d).</span></span>


## <a name="query-operators"></a><span data-ttu-id="a4941-123">查询运算符</span><span class="sxs-lookup"><span data-stu-id="a4941-123">Query Operators</span></span>
<span data-ttu-id="a4941-124">查询运算符，可以指定的查询、 查询的详细信息如条件置于要返回的记录，或指定结果的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="a4941-124">Query operators enable you to specify the details of the query, such as to put criteria on records to be returned, or specify the sorting order of results.</span></span> <span data-ttu-id="a4941-125">查询源必须支持查询运算符。</span><span class="sxs-lookup"><span data-stu-id="a4941-125">The query source must support the query operator.</span></span> <span data-ttu-id="a4941-126">如果你尝试使用不受支持的查询运算符，`System.NotSupportedException`将引发。</span><span class="sxs-lookup"><span data-stu-id="a4941-126">If you attempt to use an unsupported query operator, `System.NotSupportedException` will be thrown.</span></span>

<span data-ttu-id="a4941-127">在查询表达式中允许将其转换为 SQL 的表达式。</span><span class="sxs-lookup"><span data-stu-id="a4941-127">Only expressions that can be translated to SQL are allowed in query expressions.</span></span> <span data-ttu-id="a4941-128">例如，不包括函数调用表达式中时允许你使用`where`查询运算符。</span><span class="sxs-lookup"><span data-stu-id="a4941-128">For example, no function calls are allowed in the expressions when you use the `where` query operator.</span></span>

<span data-ttu-id="a4941-129">表 1 显示可用的查询运算符。</span><span class="sxs-lookup"><span data-stu-id="a4941-129">Table 1 shows available query operators.</span></span> <span data-ttu-id="a4941-130">此外，请参阅 Table2，将 SQL 查询和本主题中后面的等效 F # 查询表达式进行比较。</span><span class="sxs-lookup"><span data-stu-id="a4941-130">In addition, see Table2, which compares SQL queries and the equivalent F# query expressions later in this topic.</span></span> <span data-ttu-id="a4941-131">有些查询运算符不支持某些类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="a4941-131">Some query operators aren't supported by some type providers.</span></span> <span data-ttu-id="a4941-132">具体而言，在它支持由于 OData 中的限制的查询运算符限制 OData 类型提供程序。</span><span class="sxs-lookup"><span data-stu-id="a4941-132">In particular, the OData type provider is limited in the query operators that it supports due to limitations in OData.</span></span> <span data-ttu-id="a4941-133">有关详细信息，请参阅[ODataService 类型提供程序 （F #）](https://msdn.microsoft.com/library/bac609dd-9d12-4bf9-a662-24bdf4faa43e)。</span><span class="sxs-lookup"><span data-stu-id="a4941-133">For more information, see [ODataService Type Provider (F#)](https://msdn.microsoft.com/library/bac609dd-9d12-4bf9-a662-24bdf4faa43e).</span></span>

<span data-ttu-id="a4941-134">此表假定数据库采用以下形式：</span><span class="sxs-lookup"><span data-stu-id="a4941-134">This table assumes a database in the following form:</span></span>

![示例数据库关系图](../media/StudentCourseDB.png)

<span data-ttu-id="a4941-136">下面的表中的代码还假定以下数据库连接代码。</span><span class="sxs-lookup"><span data-stu-id="a4941-136">The code in the tables that follow also assumes the following database connection code.</span></span> <span data-ttu-id="a4941-137">项目应添加对 System.Data、 System.Data.Linq 和 FSharp.Data.TypeProviders 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="a4941-137">Projects should add references to System.Data,  System.Data.Linq, and FSharp.Data.TypeProviders assemblies.</span></span> <span data-ttu-id="a4941-138">创建此数据库的代码是包括在本主题的末尾。</span><span class="sxs-lookup"><span data-stu-id="a4941-138">The code that creates this database is included at the end of this topic.</span></span>

```fsharp
open System
open Microsoft.FSharp.Data.TypeProviders
open System.Data.Linq.SqlClient
open System.Linq
open Microsoft.FSharp.Linq

type schema = SqlDataConnection< @"Data Source=SERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;" >

let db = schema.GetDataContext()

// Needed for some query operator examples:
let data = [ 1; 5; 7; 11; 18; 21]
```

### <a name="table-1-query-operators"></a><span data-ttu-id="a4941-139">表 1.</span><span class="sxs-lookup"><span data-stu-id="a4941-139">Table 1.</span></span> <span data-ttu-id="a4941-140">查询运算符</span><span class="sxs-lookup"><span data-stu-id="a4941-140">Query Operators</span></span>

<table style="width:100%">
  <tr>
    <th><span data-ttu-id="a4941-141">运算符</span><span class="sxs-lookup"><span data-stu-id="a4941-141">Operator</span></span></th>
    <th><span data-ttu-id="a4941-142">描述</span><span class="sxs-lookup"><span data-stu-id="a4941-142">Description</span></span></th>
  </tr>
  <tr>
  <td>`contains`</td>
<td><span data-ttu-id="a4941-143">确定所选的元素是否包含指定的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-143">Determines whether the selected elements include a specified element.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    select student.Age.Value
    contains 11
}
</code></pre>

</td>
</tr>


<tr>
  <td>`count`</td><td><span data-ttu-id="a4941-144">返回所选元素的数量。</span><span class="sxs-lookup"><span data-stu-id="a4941-144">Returns the number of selected elements.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    select student
    count
}
</code></pre>

</td></tr><tr>
<td>`last`</td><td><span data-ttu-id="a4941-145">选择所选择的到目前为止的最后一个元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-145">Selects the last element of those selected so far.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for number in data do
    last
}
</code></pre>

</td></tr><tr>
<td>`lastOrDefault`</td><td><span data-ttu-id="a4941-146">如果未找到的元素，请选择所选择的目前为止，或默认值的最后一个元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-146">Selects the last element of those selected so far, or a default value if no element is found.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for number in data do
    where (number < 0)
    lastOrDefault
}
</code></pre>

</td></tr><tr>
<td>`exactlyOne`</td><td><span data-ttu-id="a4941-147">选择选择到目前为止的单一的特定元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-147">Selects the single, specific element selected so far.</span></span> <span data-ttu-id="a4941-148">如果存在多个元素时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="a4941-148">If multiple elements are present, an exception is thrown.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where (student.StudentID = 1)
    select student
    exactlyOne
}
</code></pre>

</td></tr><tr>
<td>`exactlyOneOrDefault`</td><td><span data-ttu-id="a4941-149">如果找不到该元素，请选择所选择的目前为止，或默认值的单一的特定元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-149">Selects the single, specific element of those selected so far, or a default value if that element is not found.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where (student.StudentID = 1)
    select student
    exactlyOneOrDefault
}
</code></pre>

</td></tr><tr>
<td>`headOrDefault`</td><td><span data-ttu-id="a4941-150">如果序列不包含任何元素，请选择所选择的目前为止，或默认值的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-150">Selects the first element of those selected so far, or a default value if the sequence contains no elements.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    select student
    headOrDefault
}
</code></pre>

</td></tr><tr>
<td>`select`</td><td><span data-ttu-id="a4941-151">每个的项目到目前为止的选定元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-151">Projects each of the elements selected so far.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    select student
}
</code></pre>

</td></tr><tr>
<td>`where`</td><td><span data-ttu-id="a4941-152">选择基于指定的谓词的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-152">Selects elements based on a specified predicate.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where (student.StudentID > 4)
    select student
}
</code></pre>

</td></tr><tr>
<td>`minBy`</td><td><span data-ttu-id="a4941-153">选择到目前为止选择每个元素的值并返回生成的最小值。</span><span class="sxs-lookup"><span data-stu-id="a4941-153">Selects a value for each element selected so far and returns the minimum resulting value.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    minBy student.StudentID
}
</code></pre>

</td></tr><tr>
<td>`maxBy`</td><td><span data-ttu-id="a4941-154">选择到目前为止选择每个元素的值并返回最大结果值。</span><span class="sxs-lookup"><span data-stu-id="a4941-154">Selects a value for each element selected so far and returns the maximum resulting value.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    maxBy student.StudentID
}
</code></pre>

</td></tr><tr>
<td>`groupBy`</td><td><span data-ttu-id="a4941-155">到目前为止会根据指定的键选择器选择的元素进行分组。</span><span class="sxs-lookup"><span data-stu-id="a4941-155">Groups the elements selected so far according to a specified key selector.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    groupBy student.Age into g
    select (g.Key, g.Count())
}
</code></pre>

</td></tr><tr>
<td>`sortBy`</td><td><span data-ttu-id="a4941-156">以升序为止选择给定的排序键的元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="a4941-156">Sorts the elements selected so far in ascending order by the given sorting key.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sortBy student.Name
    select student
}
</code></pre>

</td></tr><tr>
<td>`sortByDescending`</td><td><span data-ttu-id="a4941-157">按降序到目前为止选择给定的排序键的元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="a4941-157">Sorts the elements selected so far in descending order by the given sorting key.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sortByDescending student.Name
    select student
}
</code></pre>

</td></tr><tr>
<td>`thenBy`</td><td><span data-ttu-id="a4941-158">执行后续排序以升序为止选择给定的排序键的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-158">Performs a subsequent ordering of the elements selected so far in ascending order by the given sorting key.</span></span> <span data-ttu-id="a4941-159">此运算符可能仅可用于之后`sortBy`， `sortByDescending`， `thenBy`，或`thenByDescending`。</span><span class="sxs-lookup"><span data-stu-id="a4941-159">This operator may only be used after a `sortBy`, `sortByDescending`, `thenBy`, or `thenByDescending`.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where student.Age.HasValue
    sortBy student.Age.Value
    thenBy student.Name
    select student
}
</code></pre>

</td></tr><tr>
<td>`thenByDescending`</td><td><span data-ttu-id="a4941-160">执行后续排序按降序到目前为止选择给定的排序键的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-160">Performs a subsequent ordering of the elements selected so far in descending order by the given sorting key.</span></span> <span data-ttu-id="a4941-161">此运算符可能仅可用于之后`sortBy`， `sortByDescending`， `thenBy`，或`thenByDescending`。</span><span class="sxs-lookup"><span data-stu-id="a4941-161">This operator may only be used after a `sortBy`, `sortByDescending`, `thenBy`, or `thenByDescending`.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where student.Age.HasValue
    sortBy student.Age.Value
    thenByDescending student.Name
    select student
}
</code></pre>

</td></tr><tr>
<td>`groupValBy`</td><td><span data-ttu-id="a4941-162">选择到目前为止选择每个元素的值并按给定的键的元素进行分组。</span><span class="sxs-lookup"><span data-stu-id="a4941-162">Selects a value for each element selected so far and groups the elements by the given key.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    groupValBy student.Name student.Age into g
    select (g, g.Key, g.Count())
}
</code></pre>

</td></tr><tr>
<td>`join`</td><td><span data-ttu-id="a4941-163">关联所选值基于匹配键对两个的集。</span><span class="sxs-lookup"><span data-stu-id="a4941-163">Correlates two sets of selected values based on matching keys.</span></span> <span data-ttu-id="a4941-164">请注意，围绕 = 键的顺序登录联接表达式是重要的。</span><span class="sxs-lookup"><span data-stu-id="a4941-164">Note that the order of the keys around the = sign in a join expression is significant.</span></span> <span data-ttu-id="a4941-165">在所有联接，如果行拆分后`-&gt;`符号，缩进至少必须为缩进与关键字`for`。</span><span class="sxs-lookup"><span data-stu-id="a4941-165">In all joins, if the line is split after the `-&gt;` symbol, the indentation must be indented at least as far as the keyword `for`.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    join selection in db.CourseSelection
        on (student.StudentID = selection.StudentID)
    select (student, selection)
}
</code></pre>

</td></tr><tr>
<td>`groupJoin`</td><td><span data-ttu-id="a4941-166">关联的所选值基于匹配键对两个集，并对结果进行分组。</span><span class="sxs-lookup"><span data-stu-id="a4941-166">Correlates two sets of selected values based on matching keys and groups the results.</span></span> <span data-ttu-id="a4941-167">请注意，围绕 = 键的顺序登录联接表达式是重要的。</span><span class="sxs-lookup"><span data-stu-id="a4941-167">Note that the order of the keys around the = sign in a join expression is significant.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    groupJoin courseSelection in db.CourseSelection
        on (student.StudentID = courseSelection.StudentID) into g
    for courseSelection in g do
    join course in db.Course
        on (courseSelection.CourseID = course.CourseID)
    select (student.Name, course.CourseName)
}
</code></pre>

</td></tr><tr>
<td>`leftOuterJoin`</td><td><span data-ttu-id="a4941-168">关联的所选值基于匹配键对两个集，并对结果进行分组。</span><span class="sxs-lookup"><span data-stu-id="a4941-168">Correlates two sets of selected values based on matching keys and groups the results.</span></span> <span data-ttu-id="a4941-169">如果任何组为空，则改为使用具有一个默认值组。</span><span class="sxs-lookup"><span data-stu-id="a4941-169">If any group is empty, a group with a single default value is used instead.</span></span> <span data-ttu-id="a4941-170">请注意，围绕 = 键的顺序登录联接表达式是重要的。</span><span class="sxs-lookup"><span data-stu-id="a4941-170">Note that the order of the keys around the = sign in a join expression is significant.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    leftOuterJoin selection in db.CourseSelection
        on (student.StudentID = selection.StudentID) into result
    for selection in result.DefaultIfEmpty() do
    select (student, selection)
}
</code></pre>

</td></tr><tr>
<td>`sumByNullable`</td><td><span data-ttu-id="a4941-171">选择到目前为止选择每个元素的可以为 null 值并返回这些值的总和。</span><span class="sxs-lookup"><span data-stu-id="a4941-171">Selects a nullable value for each element selected so far and returns the sum of these values.</span></span> <span data-ttu-id="a4941-172">如果任何可以为 null 不具有一个值，则忽略它。</span><span class="sxs-lookup"><span data-stu-id="a4941-172">If any nullable does not have a value, it is ignored.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sumByNullable student.Age
}
</code></pre>

</td></tr><tr>
<td>`minByNullable`</td><td><span data-ttu-id="a4941-173">选择到目前为止选择每个元素的可以为 null 值并返回这些值的最小值。</span><span class="sxs-lookup"><span data-stu-id="a4941-173">Selects a nullable value for each element selected so far and returns the minimum of these values.</span></span> <span data-ttu-id="a4941-174">如果任何可以为 null 不具有一个值，则忽略它。</span><span class="sxs-lookup"><span data-stu-id="a4941-174">If any nullable does not have a value, it is ignored.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    minByNullable student.Age
}
</code></pre>

</td></tr><tr>
<td>`maxByNullable`</td><td><span data-ttu-id="a4941-175">选择到目前为止选择每个元素的可以为 null 值并返回这些值的最大。</span><span class="sxs-lookup"><span data-stu-id="a4941-175">Selects a nullable value for each element selected so far and returns the maximum of these values.</span></span> <span data-ttu-id="a4941-176">如果任何可以为 null 不具有一个值，则忽略它。</span><span class="sxs-lookup"><span data-stu-id="a4941-176">If any nullable does not have a value, it is ignored.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    maxByNullable student.Age
}
</code></pre>

</td></tr><tr>
<td>`averageByNullable`</td><td><span data-ttu-id="a4941-177">选择到目前为止选择每个元素的可以为 null 值并返回这些值的平均值。</span><span class="sxs-lookup"><span data-stu-id="a4941-177">Selects a nullable value for each element selected so far and returns the average of these values.</span></span> <span data-ttu-id="a4941-178">如果任何可以为 null 不具有一个值，则忽略它。</span><span class="sxs-lookup"><span data-stu-id="a4941-178">If any nullable does not have a value, it is ignored.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    averageByNullable (Nullable.float student.Age)
}
</code></pre>

</td></tr><tr>
<td>`averageBy`</td><td><span data-ttu-id="a4941-179">选择到目前为止选择每个元素的值并返回这些值的平均值。</span><span class="sxs-lookup"><span data-stu-id="a4941-179">Selects a value for each element selected so far and returns the average of these values.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    averageBy (float student.StudentID)
}
</code></pre>

</td></tr><tr>
<td>`distinct`</td><td><span data-ttu-id="a4941-180">到目前为止的选定元素从选择的非重复元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-180">Selects distinct elements from the elements selected so far.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    join selection in db.CourseSelection
        on (student.StudentID = selection.StudentID)
    distinct       
}
</code></pre>

</td></tr><tr>
<td>`exists`</td><td><span data-ttu-id="a4941-181">确定为止选择任何元素是否满足条件。</span><span class="sxs-lookup"><span data-stu-id="a4941-181">Determines whether any element selected so far satisfies a condition.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where
        (query {
            for courseSelection in db.CourseSelection do
            exists (courseSelection.StudentID = student.StudentID) })
    select student
}
</code></pre>

</td></tr><tr>
<td>`find`</td><td><span data-ttu-id="a4941-182">选择满足指定的条件的第一个元素到目前为止选择。</span><span class="sxs-lookup"><span data-stu-id="a4941-182">Selects the first element selected so far that satisfies a specified condition.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    find (student.Name = "Abercrombie, Kim")
}
</code></pre>

</td></tr><tr>
<td>`all`</td><td><span data-ttu-id="a4941-183">确定选定到目前为止的所有元素是否都满足条件。</span><span class="sxs-lookup"><span data-stu-id="a4941-183">Determines whether all elements selected so far satisfy a condition.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    all (SqlMethods.Like(student.Name, "%,%"))
}
</code></pre>

</td></tr><tr>
<td>`head`</td><td><span data-ttu-id="a4941-184">从所选择的为止选择的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-184">Selects the first element from those selected so far.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    head
}
</code></pre>

</td></tr><tr>
<td>`nth`</td><td><span data-ttu-id="a4941-185">到目前为止选择在这些所选的指定索引处的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-185">Selects the element at a specified index amongst those selected so far.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for numbers in data do
    nth 3
}
</code></pre>

</td></tr><tr>
<td>`skip`</td><td><span data-ttu-id="a4941-186">跳过指定的数量的到目前为止的选定元素，然后选择剩余的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-186">Bypasses a specified number of the elements selected so far and then selects the remaining elements.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    skip 1
}
</code></pre>

</td></tr><tr>
<td>`skipWhile`</td><td><span data-ttu-id="a4941-187">只要指定的条件为 true，然后选择剩余的元素，跳过序列中的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-187">Bypasses elements in a sequence as long as a specified condition is true and then selects the remaining elements.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for number in data do
    skipWhile (number < 3)
    select student
}
</code></pre>

</td></tr><tr>
<td>`sumBy`</td><td><span data-ttu-id="a4941-188">选择到目前为止选择每个元素的值并返回这些值的总和。</span><span class="sxs-lookup"><span data-stu-id="a4941-188">Selects a value for each element selected so far and returns the sum of these values.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sumBy student.StudentID
}
</code></pre>

</td></tr><tr>
<td>`take`</td><td><span data-ttu-id="a4941-189">到目前为止选择从这些所选的指定的数量的连续元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-189">Selects a specified number of contiguous elements from those selected so far.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    select student
    take 2
}
</code></pre>

</td></tr><tr>
<td>`takeWhile`</td><td><span data-ttu-id="a4941-190">只要指定的条件为 true，，然后跳过剩余元素，请从序列中选择元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-190">Selects elements from a sequence as long as a specified condition is true, and then skips the remaining elements.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for number in data do
    takeWhile (number < 10)
}
</code></pre>

</td></tr><tr>
<td>`sortByNullable`</td><td><span data-ttu-id="a4941-191">以升序为止选择给定可以为 null 的排序键的元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="a4941-191">Sorts the elements selected so far in ascending order by the given nullable sorting key.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sortByNullable student.Age
    select student
}
</code></pre>

</td></tr><tr>
<td>`sortByNullableDescending`</td><td><span data-ttu-id="a4941-192">按降序到目前为止选择给定可以为 null 的排序键的元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="a4941-192">Sorts the elements selected so far in descending order by the given nullable sorting key.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sortByNullableDescending student.Age
    select student
}
</code></pre>

</td></tr><tr>
<td>`thenByNullable`</td><td><span data-ttu-id="a4941-193">执行后续排序以升序为止选择给定可以为 null 的排序键的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-193">Performs a subsequent ordering of the elements selected so far in ascending order by the given nullable sorting key.</span></span> <span data-ttu-id="a4941-194">此运算符只能紧跟`sortBy`， `sortByDescending`， `thenBy`，或`thenByDescending`，或它们可以为 null 的变量。</span><span class="sxs-lookup"><span data-stu-id="a4941-194">This operator may only be used immediately after a `sortBy`, `sortByDescending`, `thenBy`, or `thenByDescending`, or their nullable variants.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sortBy student.Name
    thenByNullable student.Age
    select student
}
</code></pre>

</td></tr><tr>
<td>`thenByNullableDescending`</td><td><span data-ttu-id="a4941-195">执行后续排序按降序到目前为止选择给定可以为 null 的排序键的元素。</span><span class="sxs-lookup"><span data-stu-id="a4941-195">Performs a subsequent ordering of the elements selected so far in descending order by the given nullable sorting key.</span></span> <span data-ttu-id="a4941-196">此运算符只能紧跟`sortBy`， `sortByDescending`， `thenBy`，或`thenByDescending`，或它们可以为 null 的变量。</span><span class="sxs-lookup"><span data-stu-id="a4941-196">This operator may only be used immediately after a `sortBy`, `sortByDescending`, `thenBy`, or `thenByDescending`, or their nullable variants.</span></span><br/><br/>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    sortBy student.Name
    thenByNullableDescending student.Age
    select student
}
</code></pre>

</td></tr>
</table>

## <a name="comparison-of-transact-sql-and-f-query-expressions"></a><span data-ttu-id="a4941-197">Transact-SQL 和 F# 查询表达式的比较</span><span class="sxs-lookup"><span data-stu-id="a4941-197">Comparison of Transact-SQL and F# Query Expressions</span></span>
<span data-ttu-id="a4941-198">下表显示 F # 中的一些常见的 TRANSACT-SQL 查询和它们的等效项。</span><span class="sxs-lookup"><span data-stu-id="a4941-198">The following table shows some common Transact-SQL queries and their equivalents in F#.</span></span> <span data-ttu-id="a4941-199">此表中的代码还假定与上表和相同的初始代码来设置类型提供程序相同的数据库。</span><span class="sxs-lookup"><span data-stu-id="a4941-199">The code in this table also assumes the same database as the previous table and the same initial code to set up the type provider.</span></span>


### <a name="table-2-transact-sql-and-f-query-expressions"></a><span data-ttu-id="a4941-200">表 2。</span><span class="sxs-lookup"><span data-stu-id="a4941-200">Table 2.</span></span> <span data-ttu-id="a4941-201">Transact-SQL 和 F# 查询表达式</span><span class="sxs-lookup"><span data-stu-id="a4941-201">Transact-SQL and F# Query Expressions</span></span>


<table style="width:100%">
  <tr>
    <th><span data-ttu-id="a4941-202">TRANSACT-SQL 的 （不区分大小写）</span><span class="sxs-lookup"><span data-stu-id="a4941-202">Transact-SQL (not case sensitive)</span></span></th>
    <th><span data-ttu-id="a4941-203">F # 查询表达式 （区分大小写）</span><span class="sxs-lookup"><span data-stu-id="a4941-203">F# Query Expression (case sensitive)</span></span></th>
  </tr>
<tr><td>
<span data-ttu-id="a4941-204">从表中选择所有字段。</span><span class="sxs-lookup"><span data-stu-id="a4941-204">Select all fields from table.</span></span></br>

<pre><code class="lang-sql">SELECT * FROM Student
</code></pre>

</td><td>
<pre><code class="lang-fsharp">// All students.
query {
    for student in db.Student do
    select student
}
</code></pre>

</td></tr>
<tr><td>
<span data-ttu-id="a4941-205">计数表中的记录。</span><span class="sxs-lookup"><span data-stu-id="a4941-205">Count records in a table.</span></span><br/>

<pre><code class="lang-sql">SELECT COUNT( * ) FROM Student
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Count of students.
query {
    for student in db.Student do       
    count
}
</code></pre>

</td></tr><tr>
<td>`EXISTS`
</br>

<pre><code class="lang-sql">SELECT * FROM Student
WHERE EXISTS
  (SELECT * FROM CourseSelection
   WHERE CourseSelection.StudentID = Student.StudentID)
</code></pre>
</td>

<td>

<pre><code class="lang-fsharp">// Find students who have signed up at least one course.
query {
    for student in db.Student do
    where
        (query {
            for courseSelection in db.CourseSelection do
            exists (courseSelection.StudentID = student.StudentID) })
    select student
}
</code></pre>

</td></tr><tr>
<td><span data-ttu-id="a4941-206">分组</span><span class="sxs-lookup"><span data-stu-id="a4941-206">Grouping</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Age, COUNT( * ) FROM Student
GROUP BY Student.Age
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Group by age and count.
query {
    for n in db.Student do
    groupBy n.Age into g
    select (g.Key, g.Count())
}
// OR
query {
    for n in db.Student do
    groupValBy n.Age n.Age into g
    select (g.Key, g.Count())
}
</code></pre>
</td></tr><tr><td>
<span data-ttu-id="a4941-207">分组条件。</span><span class="sxs-lookup"><span data-stu-id="a4941-207">Grouping with condition.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Age, COUNT( * )
FROM Student
GROUP BY Student.Age
HAVING student.Age > 10
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Group students by age where age > 10.
query {
    for student in db.Student do
    groupBy student.Age into g
    where (g.Key.HasValue && g.Key.Value > 10)
    select (g.Key, g.Count())
}
</code></pre>

</td></tr><tr><td>
<span data-ttu-id="a4941-208">具有计数条件分组。</span><span class="sxs-lookup"><span data-stu-id="a4941-208">Grouping with count condition.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Age, COUNT( * )
FROM Student
GROUP BY Student.Age
HAVING COUNT( * ) > 1
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Group students by age and count number of students
// at each age with more than 1 student.
query {
    for student in db.Student do
    groupBy student.Age into group
    where (group.Count() > 1)
    select (group.Key, group.Count())
}
</code></pre>

</td></tr><tr><td>
<span data-ttu-id="a4941-209">分组、 计数，和求和。</span><span class="sxs-lookup"><span data-stu-id="a4941-209">Grouping, counting, and summing.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Age, COUNT( * ), SUM(Student.Age) as total
FROM Student
GROUP BY Student.Age
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Group students by age and sum ages.
query {
    for student in db.Student do
    groupBy student.Age into g       
    let total =
        query {
            for student in g do
            sumByNullable student.Age
        }
    select (g.Key, g.Count(), total)
}
</code></pre>

</td></tr><tr><td>
<span data-ttu-id="a4941-210">分组、 计数，并按计数进行排序。</span><span class="sxs-lookup"><span data-stu-id="a4941-210">Grouping, counting, and ordering by count.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Age, COUNT( * ) as myCount
FROM Student
GROUP BY Student.Age
HAVING COUNT( * ) > 1
ORDER BY COUNT( * ) DESC
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Group students by age, count number of students
// at each age, and display all with count > 1
// in descending order of count.
query {
    for student in db.Student do
    groupBy student.Age into g
    where (g.Count() > 1)       
    sortByDescending (g.Count())
    select (g.Key, g.Count())
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-211">
`IN`一组指定的值</span><span class="sxs-lookup"><span data-stu-id="a4941-211">
`IN` a set of specified values</span></span><br/>

<pre><code class="lang-sql">SELECT *
FROM Student
WHERE Student.StudentID IN (1, 2, 5, 10)
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Select students where studentID is one of a given list.
let idQuery =
    query {
        for id in [1; 2; 5; 10] do
        select id
    }
query {
    for student in db.Student do
    where (idQuery.Contains(student.StudentID))
    select student
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-212">
`LIKE` 和 `TOP`。</span><span class="sxs-lookup"><span data-stu-id="a4941-212">
`LIKE` and `TOP`.</span></span><br/>

<pre><code class="lang-sql">-- '_e%' matches strings where the second character is 'e'
SELECT TOP 2 * FROM Student
WHERE Student.Name LIKE '_e%'
</code></pre>

</td><td>
<pre><code class="lang-fsharp">// Look for students with Name match _e% pattern and take first two.
query {
    for student in db.Student do
    where (SqlMethods.Like( student.Name, "_e%") )
    select student
    take 2
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-213">
`LIKE`与模式相匹配。</span><span class="sxs-lookup"><span data-stu-id="a4941-213">
`LIKE` with pattern match set.</span></span><br/>

<pre><code class="lang-sql">-- '[abc]%' matches strings where the first character is
-- 'a', 'b', 'c', 'A', 'B', or 'C'
SELECT * FROM Student
WHERE Student.Name LIKE '[abc]%'
</code></pre>
</td><td>

<pre><code class="lang-fsharp">query {
    for student in db.Student do
    where (SqlMethods.Like( student.Name, "[abc]%") )
    select student 
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-214">
`LIKE`具有组排除模式。</span><span class="sxs-lookup"><span data-stu-id="a4941-214">
`LIKE` with set exclusion pattern.</span></span><br/>

<pre><code class="lang-sql">-- '[^abc]%' matches strings where the first character is
-- not 'a', 'b', 'c', 'A', 'B', or 'C'
SELECT * FROM Student
WHERE Student.Name LIKE '[^abc]%'
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Look for students with name matching [^abc]%% pattern.
query {
    for student in db.Student do
    where (SqlMethods.Like( student.Name, "[^abc]%") )
    select student
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-215">
`LIKE`上一个字段，但又选择不同的字段。</span><span class="sxs-lookup"><span data-stu-id="a4941-215">
`LIKE` on one field, but select a different field.</span></span><br/>

<pre><code class="lang-sql">SELECT StudentID AS ID FROM Student
WHERE Student.Name LIKE '[^abc]%'
</code></pre>

</td><td>

<pre><code class="lang-fsharp">query {
    for n in db.Student do
    where (SqlMethods.Like( n.Name, "[^abc]%") )
    select n.StudentID   
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-216">`LIKE`使用子字符串搜索。</span><span class="sxs-lookup"><span data-stu-id="a4941-216">`LIKE`, with substring search.</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student
WHERE Student.Name like '%A%'
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Using Contains as a query filter.
query {
    for student in db.Student do
    where (student.Name.Contains("a"))
    select student
}
</code></pre>

</td></tr><tr><td>
<span data-ttu-id="a4941-217">简单`JOIN`包含两个表。</span><span class="sxs-lookup"><span data-stu-id="a4941-217">Simple `JOIN` with two tables.</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student
JOIN CourseSelection
ON Student.StudentID = CourseSelection.StudentID
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Join Student and CourseSelection tables.
query {
    for student in db.Student do
    join selection in db.CourseSelection
        on (student.StudentID = selection.StudentID)
    select (student, selection)
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-218">`LEFT JOIN`包含两个表。</span><span class="sxs-lookup"><span data-stu-id="a4941-218">`LEFT JOIN` with two tables.</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student
LEFT JOIN CourseSelection
ON Student.StudentID = CourseSelection.StudentID
</code></pre>

</td><td>

<pre><code class="lang-fsharp">//Left Join Student and CourseSelection tables.
query {
    for student in db.Student do
    leftOuterJoin selection in db.CourseSelection
        on (student.StudentID = selection.StudentID) into result
    for selection in result.DefaultIfEmpty() do
    select (student, selection)
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-219">`JOIN`与`COUNT`</span><span class="sxs-lookup"><span data-stu-id="a4941-219">`JOIN` with `COUNT`</span></span><br/>

<pre><code class="lang-sql">SELECT COUNT( * ) FROM Student
JOIN CourseSelection
ON Student.StudentID = CourseSelection.StudentID
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Join with count.
query {
    for n in db.Student do
    join e in db.CourseSelection
        on (n.StudentID = e.StudentID)
    count
}
</code></pre>

</td></tr><tr><td>`DISTINCT`<br/>

<pre><code class="lang-sql">SELECT DISTINCT StudentID FROM CourseSelection
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Join with distinct.
query {
    for student in db.Student do
    join selection in db.CourseSelection
        on (student.StudentID = selection.StudentID)
    distinct
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-220">非重复计数。</span><span class="sxs-lookup"><span data-stu-id="a4941-220">Distinct count.</span></span><br/>

<pre><code class="lang-sql">SELECT DISTINCT COUNT(StudentID) FROM CourseSelection
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Join with distinct and count.
query {
    for n in db.Student do
    join e in db.CourseSelection
        on (n.StudentID = e.StudentID)
    distinct
    count
}
</code></pre>

</td></tr><tr><td>`BETWEEN`<br/>

<pre><code class="lang-sql">SELECT * FROM Student
WHERE Student.Age BETWEEN 10 AND 15
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Selecting students with ages between 10 and 15.
query {
    for student in db.Student do
    where (student.Age ?>= 10 && student.Age ?< 15)
    select student
}
</code></pre>

</td></tr><tr><td>`OR`<br/>

<pre><code class="lang-sql">SELECT * FROM Student
WHERE Student.Age = 11 OR Student.Age = 12
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Selecting students with age that's either 11 or 12.
query {
    for student in db.Student do
    where (student.Age.Value = 11 &#124;&#124; student.Age.Value = 12)
    select student
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-221">`OR`与排序</span><span class="sxs-lookup"><span data-stu-id="a4941-221">`OR` with ordering</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student
WHERE Student.Age = 12 OR Student.Age = 13
ORDER BY Student.Age DESC
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Selecting students in a certain age range and sorting.
query {
    for n in db.Student do
    where (n.Age.Value = 12 &#124;&#124; n.Age.Value = 13)
    sortByNullableDescending n.Age
    select n
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-222">`TOP``OR`，和排序。</span><span class="sxs-lookup"><span data-stu-id="a4941-222">`TOP`, `OR`, and ordering.</span></span><br/>

<pre><code class="lang-sql">SELECT TOP 2 student.Name FROM Student
WHERE Student.Age = 11 OR Student.Age = 12
ORDER BY Student.Name DESC
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Selecting students with certain ages,
// taking account of the possibility of nulls.
query {
    for student in db.Student do
    where
        ((student.Age.HasValue && student.Age.Value = 11) &#124;&#124;
         (student.Age.HasValue && student.Age.Value = 12))
    sortByDescending student.Name
    select student.Name
    take 2
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-223">`UNION`两个查询。</span><span class="sxs-lookup"><span data-stu-id="a4941-223">`UNION` of two queries.</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student
UNION
SELECT * FROM lastStudent
</code></pre>

</td><td>

<pre><code class="lang-fsharp">
let query1 =
    query {
        for n in db.Student do
        select (n.Name, n.Age)
    }

let query2 =
    query {
        for n in db.LastStudent do
        select (n.Name, n.Age)
    }

query2.Union (query1)
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-224">两个查询的交集。</span><span class="sxs-lookup"><span data-stu-id="a4941-224">Intersection of two queries.</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student
INTERSECT
SELECT * FROM LastStudent
</code></pre>
</td><td>

<pre><code class="lang-fsharp">
let query1 =
    query {
        for n in db.Student do
        select (n.Name, n.Age)
    }

let query2 =
    query {
        for n in db.LastStudent do
        select (n.Name, n.Age)
    }

query1.Intersect(query2)
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-225">`CASE`条件。</span><span class="sxs-lookup"><span data-stu-id="a4941-225">`CASE` condition.</span></span><br/>

<pre><code class="lang-sql">SELECT student.StudentID,
CASE Student.Age
  WHEN -1 THEN 100
  ELSE Student.Age
END,
Student.Age
FROM Student
</code></pre>

</td><td>
<pre><code class="lang-fsharp">// Using if statement to alter results for special value.
query {
    for student in db.Student do
    select
        (if student.Age.HasValue && student.Age.Value = -1 then
             (student.StudentID, System.Nullable<int>(100), student.Age)
         else (student.StudentID, student.Age, student.Age))
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-226">多个用例。</span><span class="sxs-lookup"><span data-stu-id="a4941-226">Multiple cases.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.StudentID,
CASE Student.Age
  WHEN -1 THEN 100
  WHEN 0 THEN 1000
  ELSE Student.Age
END,
Student.Age
FROM Student
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Using if statement to alter results for special values.
query {
    for student in db.Student do
    select
        (if student.Age.HasValue && student.Age.Value = -1 then
             (student.StudentID, System.Nullable<int>(100), student.Age)
         elif student.Age.HasValue && student.Age.Value = 0 then
             (student.StudentID, System.Nullable<int>(1000), student.Age)
         else (student.StudentID, student.Age, student.Age))
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-227">多个表。</span><span class="sxs-lookup"><span data-stu-id="a4941-227">Multiple tables.</span></span><br/>

<pre><code class="lang-sql">SELECT * FROM Student, Course
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Multiple table select.
query {
    for student in db.Student do
    for course in db.Course do
    select (student, course)
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-228">多个联接。</span><span class="sxs-lookup"><span data-stu-id="a4941-228">Multiple joins.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Name, Course.CourseName
FROM Student
JOIN CourseSelection
ON CourseSelection.StudentID = Student.StudentID
JOIN Course
ON Course.CourseID = CourseSelection.CourseID
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Multiple joins.
query {
    for student in db.Student do
    join courseSelection in db.CourseSelection
        on (student.StudentID = courseSelection.StudentID)
    join course in db.Course
        on (courseSelection.CourseID = course.CourseID)
    select (student.Name, course.CourseName)
}
</code></pre>

</td></tr><tr><td><span data-ttu-id="a4941-229">多个左外部联接。</span><span class="sxs-lookup"><span data-stu-id="a4941-229">Multiple left outer joins.</span></span><br/>

<pre><code class="lang-sql">SELECT Student.Name, Course.CourseName
FROM Student
LEFT OUTER JOIN CourseSelection
ON CourseSelection.StudentID = Student.StudentID
LEFT OUTER JOIN Course
ON Course.CourseID = CourseSelection.CourseID
</code></pre>

</td><td>

<pre><code class="lang-fsharp">// Using leftOuterJoin with multiple joins.
query {
    for student in db.Student do
    leftOuterJoin courseSelection in db.CourseSelection
        on (student.StudentID = courseSelection.StudentID) into g1
    for courseSelection in g1.DefaultIfEmpty() do
    leftOuterJoin course in db.Course
        on (courseSelection.CourseID = course.CourseID) into g2
    for course in g2.DefaultIfEmpty() do
    select (student.Name, course.CourseName)
}
</code></pre>

</td></tr></table>

<span data-ttu-id="a4941-230">下面的代码可以用于创建这些示例的示例数据库。</span><span class="sxs-lookup"><span data-stu-id="a4941-230">The following code can be used to create the sample database for these examples.</span></span>

<pre><code class="lang-sql">SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase COLLATE SQL_Latin1_General_CP1_CI_AS;
GO

-- Specify a simple recovery model
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

CREATE TABLE [dbo].[Course] (
[CourseID]   INT           NOT NULL,
[CourseName] NVARCHAR (50) NOT NULL,
PRIMARY KEY CLUSTERED ([CourseID] ASC)
);

CREATE TABLE [dbo].[Student] (
[StudentID] INT           NOT NULL,
[Name]      NVARCHAR (50) NOT NULL,
[Age]       INT           NULL,
PRIMARY KEY CLUSTERED ([StudentID] ASC)
);

CREATE TABLE [dbo].[CourseSelection] (
[ID]        INT NOT NULL,
[StudentID] INT NOT NULL,
[CourseID]  INT NOT NULL,
PRIMARY KEY CLUSTERED ([ID] ASC),
CONSTRAINT [FK_CourseSelection_ToTable] FOREIGN KEY ([StudentID]) REFERENCES [dbo].[Student] ([StudentID]) ON DELETE NO ACTION ON UPDATE NO ACTION,
CONSTRAINT [FK_CourseSelection_Course_1] FOREIGN KEY ([CourseID]) REFERENCES [dbo].[Course] ([CourseID]) ON DELETE NO ACTION ON UPDATE NO ACTION
);

CREATE TABLE [dbo].[LastStudent] (
[StudentID] INT           NOT NULL,
[Name]      NVARCHAR (50) NOT NULL,
[Age]       INT           NULL,
PRIMARY KEY CLUSTERED ([StudentID] ASC)
);

-- Insert data into the tables.
USE MyDatabase
INSERT INTO Course (CourseID, CourseName)
VALUES(1, 'Algebra I');
INSERT INTO Course (CourseID, CourseName)
VALUES(2, 'Trigonometry');
INSERT INTO Course (CourseID, CourseName)
VALUES(3, 'Algebra II');
INSERT INTO Course (CourseID, CourseName)
VALUES(4, 'History');
INSERT INTO Course (CourseID, CourseName)
VALUES(5, 'English');
INSERT INTO Course (CourseID, CourseName)
VALUES(6, 'French');
INSERT INTO Course (CourseID, CourseName)
VALUES(7, 'Chinese');

INSERT INTO Student (StudentID, Name, Age)
VALUES(1, 'Abercrombie, Kim', 10);
INSERT INTO Student (StudentID, Name, Age)
VALUES(2, 'Abolrous, Hazen', 14);
INSERT INTO Student (StudentID, Name, Age)
VALUES(3, 'Hance, Jim', 12);
INSERT INTO Student (StudentID, Name, Age)
VALUES(4, 'Adams, Terry', 12);
INSERT INTO Student (StudentID, Name, Age)
VALUES(5, 'Hansen, Claus', 11);
INSERT INTO Student (StudentID, Name, Age)
VALUES(6, 'Penor, Lori', 13);
INSERT INTO Student (StudentID, Name, Age)
VALUES(7, 'Perham, Tom', 12);
INSERT INTO Student (StudentID, Name, Age)
VALUES(8, 'Peng, Yun-Feng', NULL);

INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(1, 1, 2);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(2, 1, 3);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(3, 1, 5);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(4, 2, 2);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(5, 2, 5);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(6, 2, 6);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(7, 2, 3);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(8, 3, 2);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(9, 3, 1);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(10, 4, 2);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(11, 4, 5);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(12, 4, 2);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(13, 5, 3);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(14, 5, 2);
INSERT INTO CourseSelection (ID, StudentID, CourseID)
VALUES(15, 7, 3);
</code></pre>

<span data-ttu-id="a4941-231">下面的代码包含本主题中显示的示例代码。</span><span class="sxs-lookup"><span data-stu-id="a4941-231">The following code contains  the sample code that appears in this topic.</span></span>

```fsharp
#if INTERACTIVE
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.dll"
#r "System.Data.Linq.dll"
#endif
open System
open Microsoft.FSharp.Data.TypeProviders
open System.Data.Linq.SqlClient
open System.Linq

type schema = SqlDataConnection<"Data Source=SERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = schema.GetDataContext()

let data = [1; 5; 7; 11; 18; 21]

type Nullable<'T when 'T : ( new : unit -> 'T) and 'T : struct and 'T :> ValueType > with
    member this.Print() =
        if this.HasValue then this.Value.ToString()
        else "NULL"

printfn "\ncontains query operator"
query {
    for student in db.Student do
    select student.Age.Value
    contains 11
}
|> printfn "Is at least one student age 11? %b"

printfn "\ncount query operator"
query {
    for student in db.Student do
    select student
    count
}
|> printfn "Number of students: %d"

printfn "\nlast query operator."
let num =
    query {
        for number in data do
        sortBy number
        last
    }
printfn "Last number: %d" num


open Microsoft.FSharp.Linq

printfn "\nlastOrDefault query operator."
query {
    for number in data do
    sortBy number
    lastOrDefault
}
|> printfn "lastOrDefault: %d"

printfn "\nexactlyOne query operator."
let student2 =
    query {
        for student in db.Student do
        where (student.StudentID = 1)
        select student
        exactlyOne
    }
printfn "Student with StudentID = 1 is %s" student2.Name

printfn "\nexactlyOneOrDefault query operator."
let student3 =
    query {
        for student in db.Student do
        where (student.StudentID = 1)
        select student
        exactlyOneOrDefault
    }
printfn "Student with StudentID = 1 is %s" student3.Name

printfn "\nheadOrDefault query operator."
let student4 =
    query {
        for student in db.Student do
        select student
        headOrDefault
    }
printfn "head student is %s" student4.Name

printfn "\nselect query operator."
query {
    for student in db.Student do
    select student
}
|> Seq.iter (fun student -> printfn "StudentID, Name: %d %s" student.StudentID student.Name)

printfn "\nwhere query operator."
query {
    for student in db.Student do
    where (student.StudentID > 4)
    select student
}
|> Seq.iter (fun student -> printfn "StudentID, Name: %d %s" student.StudentID student.Name)

printfn "\nminBy query operator."
let student5 =
    query {
        for student in db.Student do
        minBy student.StudentID
    }

printfn "\nmaxBy query operator."
let student6 =
    query {
        for student in db.Student do
        maxBy student.StudentID
    }

printfn "\ngroupBy query operator."
query {
    for student in db.Student do
    groupBy student.Age into g
    select (g.Key, g.Count())
}
|> Seq.iter (fun (age, count) -> printfn "Age: %s Count at that age: %d" (age.Print()) count)

printfn "\nsortBy query operator."
query {
    for student in db.Student do
    sortBy student.Name
    select student
}
|> Seq.iter (fun student -> printfn "StudentID, Name: %d %s" student.StudentID student.Name)

printfn "\nsortByDescending query operator."
query {
    for student in db.Student do
    sortByDescending student.Name
    select student
}
|> Seq.iter (fun student -> printfn "StudentID, Name: %d %s" student.StudentID student.Name)

printfn "\nthenBy query operator."
query {
    for student in db.Student do
    where student.Age.HasValue
    sortBy student.Age.Value
    thenBy student.Name
    select student
}
|> Seq.iter (fun student -> printfn "StudentID, Name: %d %s" student.Age.Value student.Name)

printfn "\nthenByDescending query operator."
query {
    for student in db.Student do
    where student.Age.HasValue
    sortBy student.Age.Value
    thenByDescending student.Name
    select student
}
|> Seq.iter (fun student -> printfn "StudentID, Name: %d %s" student.Age.Value student.Name)

printfn "\ngroupValBy query operator."
query {
    for student in db.Student do
    groupValBy student.Name student.Age into g
    select (g, g.Key, g.Count())
}
|> Seq.iter (fun (group, age, count) ->
    printfn "Age: %s Count at that age: %d" (age.Print()) count
    group |> Seq.iter (fun name -> printfn "Name: %s" name))

printfn "\n sumByNullable query operator"
query {
    for student in db.Student do
    sumByNullable student.Age
}
|> (fun sum -> printfn "Sum of ages: %s" (sum.Print()))

printfn "\n minByNullable"
query {
    for student in db.Student do
    minByNullable student.Age
}
|> (fun age -> printfn "Minimum age: %s" (age.Print()))

printfn "\n maxByNullable"
query {
    for student in db.Student do
    maxByNullable student.Age
}
|> (fun age -> printfn "Maximum age: %s" (age.Print()))

printfn "\n averageBy"
query {
    for student in db.Student do
    averageBy (float student.StudentID)
}
|> printfn "Average student ID: %f"

printfn "\n averageByNullable"
query {
    for student in db.Student do
    averageByNullable (Nullable.float student.Age)
}
|> (fun avg -> printfn "Average age: %s" (avg.Print()))

printfn "\n find query operator"
query {
    for student in db.Student do
    find (student.Name = "Abercrombie, Kim")
}
|> (fun student -> printfn "Found a match with StudentID = %d" student.StudentID)

printfn "\n all query operator"
query {
    for student in db.Student do
    all (SqlMethods.Like(student.Name, "%,%"))
}
|> printfn "Do all students have a comma in the name? %b"

printfn "\n head query operator"
query {
    for student in db.Student do
    head
}
|> (fun student -> printfn "Found the head student with StudentID = %d" student.StudentID)

printfn "\n nth query operator"
query {
    for numbers in data do
    nth 3
}
|> printfn "Third number is %d"

printfn "\n skip query operator"
query {
    for student in db.Student do
    skip 1
}
|> Seq.iter (fun student -> printfn "StudentID = %d" student.StudentID)

printfn "\n skipWhile query operator"
query {
    for number in data do
    skipWhile (number < 3)
    select number
}
|> Seq.iter (fun number -> printfn "Number = %d" number)


printfn "\n sumBy query operator"
query {
    for student in db.Student do
    sumBy student.StudentID
}
|> printfn "Sum of student IDs: %d"

printfn "\n take query operator"
query {
    for student in db.Student do
    select student
    take 2
}
|> Seq.iter (fun student -> printfn "StudentID = %d" student.StudentID)

printfn "\n takeWhile query operator"
query {
    for number in data do
    takeWhile (number < 10)
}
|> Seq.iter (fun number -> printfn "Number = %d" number)

printfn "\n sortByNullable query operator"
query {
    for student in db.Student do
    sortByNullable student.Age
    select student
}
|> Seq.iter (fun student ->
    printfn "StudentID, Name, Age: %d %s %s" student.StudentID student.Name (student.Age.Print()))

printfn "\n sortByNullableDescending query operator"
query {
    for student in db.Student do
    sortByNullableDescending student.Age
    select student
}
|> Seq.iter (fun student ->
    printfn "StudentID, Name, Age: %d %s %s" student.StudentID student.Name (student.Age.Print()))

printfn "\n thenByNullable query operator"
query {
    for student in db.Student do
    sortBy student.Name
    thenByNullable student.Age
    select student
}
|> Seq.iter (fun student ->
    printfn "StudentID, Name, Age: %d %s %s" student.StudentID student.Name (student.Age.Print()))

printfn "\n thenByNullableDescending query operator"
query {
    for student in db.Student do
    sortBy student.Name
    thenByNullableDescending student.Age
    select student
}
|> Seq.iter (fun student ->
    printfn "StudentID, Name, Age: %d %s %s" student.StudentID student.Name (student.Age.Print()))

printfn "All students: "
query {
    for student in db.Student do
    select student
}
|> Seq.iter (fun student -> printfn "%s %d %s" student.Name student.StudentID (student.Age.Print()))

printfn "\nCount of students: "
query {
    for student in db.Student do
    count
}
|> (fun count -> printfn "Student count: %d" count)

printfn "\nExists."
query {
    for student in db.Student do
    where
        (query {
            for courseSelection in db.CourseSelection do
            exists (courseSelection.StudentID = student.StudentID) })
    select student
}
|> Seq.iter (fun student -> printfn "%A" student.Name)

printfn "\n Group by age and count"
query {
    for n in db.Student do
    groupBy n.Age into g
    select (g.Key, g.Count())
}
|> Seq.iter (fun (age, count) -> printfn "%s %d" (age.Print()) count)

printfn "\n Group value by age."
query {
    for n in db.Student do
    groupValBy n.Age n.Age into g
    select (g.Key, g.Count())
}
|> Seq.iter (fun (age, count) -> printfn "%s %d" (age.Print()) count)

printfn "\nGroup students by age where age > 10."
query {
    for student in db.Student do
    groupBy student.Age into g
    where (g.Key.HasValue && g.Key.Value > 10)
    select (g, g.Key)
}
|> Seq.iter (fun (students, age) ->
    printfn "Age: %s" (age.Value.ToString())
    students
    |> Seq.iter (fun student -> printfn "%s" student.Name))

printfn "\nGroup students by age and print counts of number of students at each age with more than 1 student."
query {
    for student in db.Student do
    groupBy student.Age into group
    where (group.Count() > 1)
    select (group.Key, group.Count())
}
|> Seq.iter (fun (age, ageCount) ->
    printfn "Age: %s Count: %d" (age.Print()) ageCount)

printfn "\nGroup students by age and sum ages."
query {
    for student in db.Student do
    groupBy student.Age into g
    let total = query { for student in g do sumByNullable student.Age }
    select (g.Key, g.Count(), total)
}
|> Seq.iter (fun (age, count, total) ->
    printfn "Age: %d" (age.GetValueOrDefault())
    printfn "Count: %d" count
    printfn "Total years: %s" (total.ToString()))

printfn "\nGroup students by age and count number of students at each age, and display all with count > 1 in descending order of count."
query {
    for student in db.Student do
    groupBy student.Age into g
    where (g.Count() > 1)
    sortByDescending (g.Count())
    select (g.Key, g.Count())
}
|> Seq.iter (fun (age, myCount) ->
    printfn "Age: %s" (age.Print())
    printfn "Count: %d" myCount)

printfn "\n Select students from a set of IDs"
let idList = [1; 2; 5; 10]
let idQuery =
    query { for id in idList do select id }
query {
    for student in db.Student do
    where (idQuery.Contains(student.StudentID))
    select student
}
|> Seq.iter (fun student ->
    printfn "Name: %s" student.Name)

printfn "\nLook for students with Name match _e%% pattern and take first two."
query {
    for student in db.Student do
    where (SqlMethods.Like( student.Name, "_e%") )
    select student
    take 2
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\nLook for students with Name matching [abc]%% pattern."
query {
    for student in db.Student do
    where (SqlMethods.Like( student.Name, "[abc]%") )
    select student
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\nLook for students with name matching [^abc]%% pattern."
query {
    for student in db.Student do
    where (SqlMethods.Like( student.Name, "[^abc]%") )
    select student
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\nLook for students with name matching [^abc]%% pattern and select ID."
query {
    for n in db.Student do
    where (SqlMethods.Like( n.Name, "[^abc]%") )
    select n.StudentID
}
|> Seq.iter (fun id -> printfn "%d" id)

printfn "\n Using Contains as a query filter."
query {
    for student in db.Student do
    where (student.Name.Contains("a"))
    select student
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\nSearching for names from a list."
let names = [|"a";"b";"c"|]
query {
    for student in db.Student do
    if names.Contains (student.Name) then select student
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\nJoin Student and CourseSelection tables."
query {
    for student in db.Student do
    join selection in db.CourseSelection
        on (student.StudentID = selection.StudentID)
    select (student, selection)
}
|> Seq.iter (fun (student, selection) -> printfn "%d %s %d" student.StudentID student.Name selection.CourseID)

printfn "\nLeft Join Student and CourseSelection tables."
query {
    for student in db.Student do
    leftOuterJoin selection in db.CourseSelection
        on (student.StudentID = selection.StudentID) into result
    for selection in result.DefaultIfEmpty() do
    select (student, selection)
}
|> Seq.iter (fun (student, selection) ->
    let selectionID, studentID, courseID =
        match selection with
        | null -> "NULL", "NULL", "NULL"
        | sel -> (sel.ID.ToString(), sel.StudentID.ToString(), sel.CourseID.ToString())
    printfn "%d %s %d %s %s %s" student.StudentID student.Name (student.Age.GetValueOrDefault()) selectionID studentID courseID)

printfn "\nJoin with count"
query {
    for n in db.Student do
    join e in db.CourseSelection
        on (n.StudentID = e.StudentID)
    count
}
|> printfn "%d"

printfn "\n Join with distinct."
query {
    for student in db.Student do
    join selection in db.CourseSelection
        on (student.StudentID = selection.StudentID)
    distinct
}
|> Seq.iter (fun (student, selection) -> printfn "%s %d" student.Name selection.CourseID)

printfn "\n Join with distinct and count."
query {
    for n in db.Student do
    join e in db.CourseSelection
        on (n.StudentID = e.StudentID)
    distinct
    count
}
|> printfn "%d"

printfn "\n Selecting students with age between 10 and 15."
query {
    for student in db.Student do
    where (student.Age.Value >= 10 && student.Age.Value < 15)
    select student
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\n Selecting students with age either 11 or 12."
query {
    for student in db.Student do
    where (student.Age.Value = 11 || student.Age.Value = 12)
    select student
}
|> Seq.iter (fun student -> printfn "%s" student.Name)

printfn "\n Selecting students in a certain age range and sorting."
query {
    for n in db.Student do
    where (n.Age.Value = 12 || n.Age.Value = 13)
    sortByNullableDescending n.Age
    select n
}
|> Seq.iter (fun student -> printfn "%s %s" student.Name (student.Age.Print()))

printfn "\n Selecting students with certain ages, taking account of possibility of nulls."
query {
    for student in db.Student do
    where
        ((student.Age.HasValue && student.Age.Value = 11) ||
         (student.Age.HasValue && student.Age.Value = 12))
    sortByDescending student.Name
    select student.Name
    take 2
}
|> Seq.iter (fun name -> printfn "%s" name)

printfn "\n Union of two queries."
module Queries =
    let query1 = query {
        for n in db.Student do
        select (n.Name, n.Age)
    }

    let query2 = query {
        for n in db.LastStudent do
        select (n.Name, n.Age)
    }

    query2.Union (query1)
    |> Seq.iter (fun (name, age) -> printfn "%s %s" name (age.Print()))

printfn "\n Intersect of two queries."
module Queries2 =
    let query1 = query {
        for n in db.Student do
        select (n.Name, n.Age)
    }

    let query2 = query {
        for n in db.LastStudent do
        select (n.Name, n.Age)
    }

    query1.Intersect(query2)
    |> Seq.iter (fun (name, age) -> printfn "%s %s" name (age.Print()))

printfn "\n Using if statement to alter results for special value."
query {
    for student in db.Student do
    select
        (if student.Age.HasValue && student.Age.Value = -1 then
            (student.StudentID, System.Nullable<int>(100), student.Age)
         else (student.StudentID, student.Age, student.Age))
}
|> Seq.iter (fun (id, value, age) -> printfn "%d %s %s" id (value.Print()) (age.Print()))

printfn "\n Using if statement to alter results special values."
query {
    for student in db.Student do
    select
        (if student.Age.HasValue && student.Age.Value = -1 then
            (student.StudentID, System.Nullable<int>(100), student.Age)
         elif student.Age.HasValue && student.Age.Value = 0 then
            (student.StudentID, System.Nullable<int>(100), student.Age)
         else (student.StudentID, student.Age, student.Age))
}
|> Seq.iter (fun (id, value, age) -> printfn "%d %s %s" id (value.Print()) (age.Print()))

printfn "\n Multiple table select."
query {
    for student in db.Student do
    for course in db.Course do
    select (student, course)
}
|> Seq.iteri (fun index (student, course) ->
    if index = 0 then
        printfn "StudentID Name Age CourseID CourseName"
    printfn "%d %s %s %d %s" student.StudentID student.Name (student.Age.Print()) course.CourseID course.CourseName)

printfn "\nMultiple Joins"
query {
    for student in db.Student do
    join courseSelection in db.CourseSelection
        on (student.StudentID = courseSelection.StudentID)
    join course in db.Course
        on (courseSelection.CourseID = course.CourseID)
    select (student.Name, course.CourseName)
}
|> Seq.iter (fun (studentName, courseName) -> printfn "%s %s" studentName courseName)

printfn "\nMultiple Left Outer Joins"
query {
    for student in db.Student do
    leftOuterJoin courseSelection in db.CourseSelection
        on (student.StudentID = courseSelection.StudentID) into g1
    for courseSelection in g1.DefaultIfEmpty() do
    leftOuterJoin course in db.Course
        on (courseSelection.CourseID = course.CourseID) into g2
    for course in g2.DefaultIfEmpty() do
    select (student.Name, course.CourseName)
}
|> Seq.iter (fun (studentName, courseName) -> printfn "%s %s" studentName courseName)
```

<span data-ttu-id="a4941-232">和在 F # Interactive 中运行此代码时，以下是完整的输出。</span><span class="sxs-lookup"><span data-stu-id="a4941-232">And here is the full output when this code is run in F# Interactive.</span></span>

```
--> Referenced 'C:\Program Files (x86)\Reference Assemblies\Microsoft\FSharp\3.0\Runtime\v4.0\Type Providers\FSharp.Data.TypeProviders.dll'


--> Referenced 'C:\Windows\Microsoft.NET\Framework\v4.0.30319\System.Data.dll'


--> Referenced 'C:\Windows\Microsoft.NET\Framework\v4.0.30319\System.Data.Linq.dll'


contains query operator
Binding session to 'C:\Users\ghogen\AppData\Local\Temp\tmp5E3C.dll'...
Binding session to 'C:\Users\ghogen\AppData\Local\Temp\tmp611A.dll'...
Is at least one student age 11? true

count query operator
Number of students: 8

last query operator.
Last number: 21

lastOrDefault query operator.
lastOrDefault: 21

exactlyOne query operator.
Student with StudentID = 1 is Abercrombie, Kim

exactlyOneOrDefault query operator.
Student with StudentID = 1 is Abercrombie, Kim

headOrDefault query operator.
head student is Abercrombie, Kim

select query operator.
StudentID, Name: 1 Abercrombie, Kim
StudentID, Name: 2 Abolrous, Hazen
StudentID, Name: 3 Hance, Jim
StudentID, Name: 4 Adams, Terry
StudentID, Name: 5 Hansen, Claus
StudentID, Name: 6 Penor, Lori
StudentID, Name: 7 Perham, Tom
StudentID, Name: 8 Peng, Yun-Feng

where query operator.
StudentID, Name: 5 Hansen, Claus
StudentID, Name: 6 Penor, Lori
StudentID, Name: 7 Perham, Tom
StudentID, Name: 8 Peng, Yun-Feng

minBy query operator.

maxBy query operator.

groupBy query operator.
Age: NULL Count at that age: 1
Age: 10 Count at that age: 1
Age: 11 Count at that age: 1
Age: 12 Count at that age: 3
Age: 13 Count at that age: 1
Age: 14 Count at that age: 1

sortBy query operator.
StudentID, Name: 1 Abercrombie, Kim
StudentID, Name: 2 Abolrous, Hazen
StudentID, Name: 4 Adams, Terry
StudentID, Name: 3 Hance, Jim
StudentID, Name: 5 Hansen, Claus
StudentID, Name: 8 Peng, Yun-Feng
StudentID, Name: 6 Penor, Lori
StudentID, Name: 7 Perham, Tom

sortByDescending query operator.
StudentID, Name: 7 Perham, Tom
StudentID, Name: 6 Penor, Lori
StudentID, Name: 8 Peng, Yun-Feng
StudentID, Name: 5 Hansen, Claus
StudentID, Name: 3 Hance, Jim
StudentID, Name: 4 Adams, Terry
StudentID, Name: 2 Abolrous, Hazen
StudentID, Name: 1 Abercrombie, Kim

thenBy query operator.
StudentID, Name: 10 Abercrombie, Kim
StudentID, Name: 11 Hansen, Claus
StudentID, Name: 12 Adams, Terry
StudentID, Name: 12 Hance, Jim
StudentID, Name: 12 Perham, Tom
StudentID, Name: 13 Penor, Lori
StudentID, Name: 14 Abolrous, Hazen

thenByDescending query operator.
StudentID, Name: 10 Abercrombie, Kim
StudentID, Name: 11 Hansen, Claus
StudentID, Name: 12 Perham, Tom
StudentID, Name: 12 Hance, Jim
StudentID, Name: 12 Adams, Terry
StudentID, Name: 13 Penor, Lori
StudentID, Name: 14 Abolrous, Hazen

groupValBy query operator.
Age: NULL Count at that age: 1
Name: Peng, Yun-Feng
Age: 10 Count at that age: 1
Name: Abercrombie, Kim
Age: 11 Count at that age: 1
Name: Hansen, Claus
Age: 12 Count at that age: 3
Name: Hance, Jim
Name: Adams, Terry
Name: Perham, Tom
Age: 13 Count at that age: 1
Name: Penor, Lori
Age: 14 Count at that age: 1
Name: Abolrous, Hazen

sumByNullable query operator
Sum of ages: 84

minByNullable
Minimum age: 10

maxByNullable
Maximum age: 14

averageBy
Average student ID: 4.500000

averageByNullable
Average age: 12

find query operator
Found a match with StudentID = 1

all query operator
Do all students have a comma in the name? true

head query operator
Found the head student with StudentID = 1

nth query operator
Third number is 11

skip query operator
StudentID = 2
StudentID = 3
StudentID = 4
StudentID = 5
StudentID = 6
StudentID = 7
StudentID = 8

skipWhile query operator
Number = 5
Number = 7
Number = 11
Number = 18
Number = 21

sumBy query operator
Sum of student IDs: 36

take query operator
StudentID = 1
StudentID = 2

takeWhile query operator
Number = 1
Number = 5
Number = 7

sortByNullable query operator
StudentID, Name, Age: 8 Peng, Yun-Feng NULL
StudentID, Name, Age: 1 Abercrombie, Kim 10
StudentID, Name, Age: 5 Hansen, Claus 11
StudentID, Name, Age: 7 Perham, Tom 12
StudentID, Name, Age: 3 Hance, Jim 12
StudentID, Name, Age: 4 Adams, Terry 12
StudentID, Name, Age: 6 Penor, Lori 13
StudentID, Name, Age: 2 Abolrous, Hazen 14

sortByNullableDescending query operator
StudentID, Name, Age: 2 Abolrous, Hazen 14
StudentID, Name, Age: 6 Penor, Lori 13
StudentID, Name, Age: 7 Perham, Tom 12
StudentID, Name, Age: 3 Hance, Jim 12
StudentID, Name, Age: 4 Adams, Terry 12
StudentID, Name, Age: 5 Hansen, Claus 11
StudentID, Name, Age: 1 Abercrombie, Kim 10
StudentID, Name, Age: 8 Peng, Yun-Feng NULL

thenByNullable query operator
StudentID, Name, Age: 1 Abercrombie, Kim 10
StudentID, Name, Age: 2 Abolrous, Hazen 14
StudentID, Name, Age: 4 Adams, Terry 12
StudentID, Name, Age: 3 Hance, Jim 12
StudentID, Name, Age: 5 Hansen, Claus 11
StudentID, Name, Age: 8 Peng, Yun-Feng NULL
StudentID, Name, Age: 6 Penor, Lori 13
StudentID, Name, Age: 7 Perham, Tom 12

thenByNullableDescending query operator
StudentID, Name, Age: 1 Abercrombie, Kim 10
StudentID, Name, Age: 2 Abolrous, Hazen 14
StudentID, Name, Age: 4 Adams, Terry 12
StudentID, Name, Age: 3 Hance, Jim 12
StudentID, Name, Age: 5 Hansen, Claus 11
StudentID, Name, Age: 8 Peng, Yun-Feng NULL
StudentID, Name, Age: 6 Penor, Lori 13
StudentID, Name, Age: 7 Perham, Tom 12
All students:
Abercrombie, Kim 1 10
Abolrous, Hazen 2 14
Hance, Jim 3 12
Adams, Terry 4 12
Hansen, Claus 5 11
Penor, Lori 6 13
Perham, Tom 7 12
Peng, Yun-Feng 8 NULL

Count of students:
Student count: 8

Exists.
"Abercrombie, Kim"
"Abolrous, Hazen"
"Hance, Jim"
"Adams, Terry"
"Hansen, Claus"
"Perham, Tom"

Group by age and count
NULL 1
10 1
11 1
12 3
13 1
14 1

Group value by age.
NULL 1
10 1
11 1
12 3
13 1
14 1

Group students by age where age > 10.
Age: 11
Hansen, Claus
Age: 12
Hance, Jim
Adams, Terry
Perham, Tom
Age: 13
Penor, Lori
Age: 14
Abolrous, Hazen

Group students by age and print counts of number of students at each age with more than 1 student.
Age: 12 Count: 3

Group students by age and sum ages.
Age: 0
Count: 1
Total years:
Age: 10
Count: 1
Total years: 10
Age: 11
Count: 1
Total years: 11
Age: 12
Count: 3
Total years: 36
Age: 13
Count: 1
Total years: 13
Age: 14
Count: 1
Total years: 14

Group students by age and count number of students at each age, and display all with count > 1 in descending order of count.
Age: 12
Count: 3

Select students from a set of IDs
Name: Abercrombie, Kim
Name: Abolrous, Hazen
Name: Hansen, Claus

Look for students with Name match _e% pattern and take first two.
Penor, Lori
Perham, Tom

Look for students with Name matching [abc]% pattern.
Abercrombie, Kim
Abolrous, Hazen
Adams, Terry

Look for students with name matching [^abc]% pattern.
Hance, Jim
Hansen, Claus
Penor, Lori
Perham, Tom
Peng, Yun-Feng

Look for students with name matching [^abc]% pattern and select ID.
3
5
6
7
8

Using Contains as a query filter.
Abercrombie, Kim
Abolrous, Hazen
Hance, Jim
Adams, Terry
Hansen, Claus
Perham, Tom

Searching for names from a list.

Join Student and CourseSelection tables.
2 Abolrous, Hazen 2
3 Hance, Jim 3
5 Hansen, Claus 5
2 Abolrous, Hazen 2
5 Hansen, Claus 5
6 Penor, Lori 6
3 Hance, Jim 3
2 Abolrous, Hazen 2
1 Abercrombie, Kim 1
2 Abolrous, Hazen 2
5 Hansen, Claus 5
2 Abolrous, Hazen 2
3 Hance, Jim 3
2 Abolrous, Hazen 2
3 Hance, Jim 3

Left Join Student and CourseSelection tables.
1 Abercrombie, Kim 10 9 3 1
2 Abolrous, Hazen 14 1 1 2
2 Abolrous, Hazen 14 4 2 2
2 Abolrous, Hazen 14 8 3 2
2 Abolrous, Hazen 14 10 4 2
2 Abolrous, Hazen 14 12 4 2
2 Abolrous, Hazen 14 14 5 2
3 Hance, Jim 12 2 1 3
3 Hance, Jim 12 7 2 3
3 Hance, Jim 12 13 5 3
3 Hance, Jim 12 15 7 3
4 Adams, Terry 12 NULL NULL NULL
5 Hansen, Claus 11 3 1 5
5 Hansen, Claus 11 5 2 5
5 Hansen, Claus 11 11 4 5
6 Penor, Lori 13 6 2 6
7 Perham, Tom 12 NULL NULL NULL
8 Peng, Yun-Feng 0 NULL NULL NULL

Join with count
15

Join with distinct.
Abercrombie, Kim 2
Abercrombie, Kim 3
Abercrombie, Kim 5
Abolrous, Hazen 2
Abolrous, Hazen 5
Abolrous, Hazen 6
Abolrous, Hazen 3
Hance, Jim 2
Hance, Jim 1
Adams, Terry 2
Adams, Terry 5
Adams, Terry 2
Hansen, Claus 3
Hansen, Claus 2
Perham, Tom 3

Join with distinct and count.
15

Selecting students with age between 10 and 15.
Abercrombie, Kim
Abolrous, Hazen
Hance, Jim
Adams, Terry
Hansen, Claus
Penor, Lori
Perham, Tom

Selecting students with age either 11 or 12.
Hance, Jim
Adams, Terry
Hansen, Claus
Perham, Tom

Selecting students in a certain age range and sorting.
Penor, Lori 13
Perham, Tom 12
Hance, Jim 12
Adams, Terry 12

Selecting students with certain ages, taking account of possibility of nulls.
Hance, Jim
Adams, Terry

Union of two queries.
Abercrombie, Kim 10
Abolrous, Hazen 14
Hance, Jim 12
Adams, Terry 12
Hansen, Claus 11
Penor, Lori 13
Perham, Tom 12
Peng, Yun-Feng NULL

Intersect of two queries.

Using if statement to alter results for special value.
1 10 10
2 14 14
3 12 12
4 12 12
5 11 11
6 13 13
7 12 12
8 NULL NULL

Using if statement to alter results special values.
1 10 10
2 14 14
3 12 12
4 12 12
5 11 11
6 13 13
7 12 12
8 NULL NULL

Multiple table select.
StudentID Name Age CourseID CourseName
1 Abercrombie, Kim 10 1 Algebra I
2 Abolrous, Hazen 14 1 Algebra I
3 Hance, Jim 12 1 Algebra I
4 Adams, Terry 12 1 Algebra I
5 Hansen, Claus 11 1 Algebra I
6 Penor, Lori 13 1 Algebra I
7 Perham, Tom 12 1 Algebra I
8 Peng, Yun-Feng NULL 1 Algebra I
1 Abercrombie, Kim 10 2 Trigonometry
2 Abolrous, Hazen 14 2 Trigonometry
3 Hance, Jim 12 2 Trigonometry
4 Adams, Terry 12 2 Trigonometry
5 Hansen, Claus 11 2 Trigonometry
6 Penor, Lori 13 2 Trigonometry
7 Perham, Tom 12 2 Trigonometry
8 Peng, Yun-Feng NULL 2 Trigonometry
1 Abercrombie, Kim 10 3 Algebra II
2 Abolrous, Hazen 14 3 Algebra II
3 Hance, Jim 12 3 Algebra II
4 Adams, Terry 12 3 Algebra II
5 Hansen, Claus 11 3 Algebra II
6 Penor, Lori 13 3 Algebra II
7 Perham, Tom 12 3 Algebra II
8 Peng, Yun-Feng NULL 3 Algebra II
1 Abercrombie, Kim 10 4 History
2 Abolrous, Hazen 14 4 History
3 Hance, Jim 12 4 History
4 Adams, Terry 12 4 History
5 Hansen, Claus 11 4 History
6 Penor, Lori 13 4 History
7 Perham, Tom 12 4 History
8 Peng, Yun-Feng NULL 4 History
1 Abercrombie, Kim 10 5 English
2 Abolrous, Hazen 14 5 English
3 Hance, Jim 12 5 English
4 Adams, Terry 12 5 English
5 Hansen, Claus 11 5 English
6 Penor, Lori 13 5 English
7 Perham, Tom 12 5 English
8 Peng, Yun-Feng NULL 5 English
1 Abercrombie, Kim 10 6 French
2 Abolrous, Hazen 14 6 French
3 Hance, Jim 12 6 French
4 Adams, Terry 12 6 French
5 Hansen, Claus 11 6 French
6 Penor, Lori 13 6 French
7 Perham, Tom 12 6 French
8 Peng, Yun-Feng NULL 6 French
1 Abercrombie, Kim 10 7 Chinese
2 Abolrous, Hazen 14 7 Chinese
3 Hance, Jim 12 7 Chinese
4 Adams, Terry 12 7 Chinese
5 Hansen, Claus 11 7 Chinese
6 Penor, Lori 13 7 Chinese
7 Perham, Tom 12 7 Chinese
8 Peng, Yun-Feng NULL 7 Chinese

Multiple Joins
Abercrombie, Kim Trigonometry
Abercrombie, Kim Algebra II
Abercrombie, Kim English
Abolrous, Hazen Trigonometry
Abolrous, Hazen English
Abolrous, Hazen French
Abolrous, Hazen Algebra II
Hance, Jim Trigonometry
Hance, Jim Algebra I
Adams, Terry Trigonometry
Adams, Terry English
Adams, Terry Trigonometry
Hansen, Claus Algebra II
Hansen, Claus Trigonometry
Perham, Tom Algebra II

Multiple Left Outer Joins
Abercrombie, Kim Trigonometry
Abercrombie, Kim Algebra II
Abercrombie, Kim English
Abolrous, Hazen Trigonometry
Abolrous, Hazen English
Abolrous, Hazen French
Abolrous, Hazen Algebra II
Hance, Jim Trigonometry
Hance, Jim Algebra I
Adams, Terry Trigonometry
Adams, Terry English
Adams, Terry Trigonometry
Hansen, Claus Algebra II
Hansen, Claus Trigonometry
Penor, Lori
Perham, Tom Algebra II
Peng, Yun-Feng

type schema
val db : schema.ServiceTypes.SimpleDataContextTypes.MyDatabase1
val student : System.Data.Linq.Table<schema.ServiceTypes.Student>
val data : int list = [1; 5; 7; 11; 18; 21]
type Nullable<'T
                when 'T : (new : unit ->  'T) and 'T : struct and
                     'T :> System.ValueType> with
  member Print : unit -> string
val num : int = 21
val student2 : schema.ServiceTypes.Student
val student3 : schema.ServiceTypes.Student
val student4 : schema.ServiceTypes.Student
val student5 : int = 1
val student6 : int = 8
val idList : int list = [1; 2; 5; 10]
val idQuery : seq<int>
val names : string [] = [|"a"; "b"; "c"|]
module Queries = begin
  val query1 : System.Linq.IQueryable<string * System.Nullable<int>>
  val query2 : System.Linq.IQueryable<string * System.Nullable<int>>
end
module Queries2 = begin
  val query1 : System.Linq.IQueryable<string * System.Nullable<int>>
  val query2 : System.Linq.IQueryable<string * System.Nullable<int>>
end
```

## <a name="see-also"></a><span data-ttu-id="a4941-233">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4941-233">See Also</span></span>
[<span data-ttu-id="a4941-234">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="a4941-234">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a4941-235">Linq.QueryBuilder 类</span><span class="sxs-lookup"><span data-stu-id="a4941-235">Linq.QueryBuilder Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d)

[<span data-ttu-id="a4941-236">计算表达式</span><span class="sxs-lookup"><span data-stu-id="a4941-236">Computation Expressions</span></span>](Computation-Expressions.md)