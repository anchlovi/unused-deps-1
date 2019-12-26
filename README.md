# unused-deps-1
False-positive repro rules_scala unused deps

In this repo there are 3 targets:

<table>
<thead>
<tr>
<th>Target</th>
<th>Rule Type</th>
<th>Dependencies</th>
</tr>
</thead>
<tbody>
<tr>
<td>b1</td>
<td>scala_library</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>b2</td>
<td>scala_library</td>
<td>b3</td>
</tr>
<tr>
<td>b3</td>
<td>scala_library</td>
<td>&nbsp;</td>
</tr>
</tbody>
</table>

Target `b3` consist of a single src file - [java interface](src/main/scala/com/comp/b3/B3.java)

Target `b2` [depends](src/main/scala/com/comp/b2/BUILD.bazel#L7) and [uses](src/main/scala/com/comp/b2/B2.scala#L6) `b3` java interface

Running build with unused deps on `warn`, the output is:
```
INFO: From scala //src/main/scala/com/comp/b2:b2:
warning: Target '//src/main/scala/com/comp/b3:b3' is specified as a dependency to //src/main/scala/com/comp/b2:b2 but isn't used, please remove it from the deps.
You can use the following buildozer command:
buildozer 'remove deps //src/main/scala/com/comp/b3:b3' //src/main/scala/com/comp/b2:b2
one warning found
```
