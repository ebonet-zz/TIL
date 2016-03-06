### [Android] Customizing Android Studio Setter Generator to create Chainable Setters

I like chainable methods. I really do. Just look at the builder pattern, how sexy is that.

For me, no methods should return void. Void is useless. You can do nothing with void.
Instead, why not make the function return the object instead of void. This way, instead of:

```java
  Obj = new Obj();
  obj.setProp1(prop1);
  obj.setProp2(prop2);
  obj.setProp3(prop3);
```

We could have:

```java
  Obj = new Obj().setProp1(prop1).setProp2(prop2).setProp3(prop3);
```

Creating getters/setters is a really boring process, and luckily IntelliJ/Android Studio
generate those automagically. But returning void. Happily, those guys at JetBrains
made everything in their platforms customizable, even code generation. So let's change that.

Opening the `Insert | Setters` dialog, you can select the template of the setter, and by the right
you have `...`. Click that.

Check out the `IntelliJ Default` template:

```
#set($paramName = $helper.getParamName($field, $project))
public ##
#if($field.modifierStatic)
static ##
#end
void set$StringUtil.capitalizeWithJavaBeanConvention($StringUtil.sanitizeJavaIdentifier($helper.getPropertyName($field, $project)))($field.type $paramName) {
#if ($field.name == $paramName)
  #if (!$field.modifierStatic)
    this.##
  #else
    $classname.##
  #end
#end
$field.name = $paramName;
}
```
