# Intro to ScriptableObjects

ScriptableObjects are a very powerful system in Unity that allows developers to store and load preset data in an easily managed way. This tutorial will cover the basics of creating a ScriptableObject and creating/storing data with them. These concepts will be explored through creating a system for storing Pokemon information.

1. Create a new C# script, and call it Pokemon.cs
   
![img.png](https://cdn.discordapp.com/attachments/675897969005953037/1344033469155639347/image.png?ex=67bf7035&is=67be1eb5&hm=3d8a3854a5683d9a647c3cc65130a8b1317484c5ff76d297307930381f221354&)
![img.png](https://cdn.discordapp.com/attachments/675897969005953037/1344033686701478070/image.png?ex=67bf7069&is=67be1ee9&hm=51fb3a03184faf8bde128bf4873a74fccfb011183c73a4971edde2638315da6d&)

```csharp
public class Pokemon : MonoBehaviour
{

}
```

2. Change 'MonoBehaviour' to 'ScriptableObject'

```csharp
public class Pokemon : ScriptableObject
{

}
```

3. Add a 'CreateAssetMenu' tag. This will allow us to create 'versions' of Pokemon later in the tutorial.

```csharp
[CreateAssetMenu(fileName = "Pokemon", menuName = "ScriptableObjects/Pokemon")]
public class Pokemon : ScriptableObject
{

}
```

4. Now we have to add some data to the scriptable object. Start by creating a "PokemonType" enum.

```csharp
[CreateAssetMenu(fileName = "Pokemon", menuName = "ScriptableObjects/Pokemon")]
public class Pokemon : ScriptableObject
{
    
}

public enum PokemonType
{
    Grass,
    Water,
    Fire
}
```

5. In order for properties to show up when we create this ScriptableObject, they have to be serialized. Add a serialized field with the type of the Pokemon.

```csharp
[CreateAssetMenu(fileName = "Pokemon", menuName = "ScriptableObjects/Pokemon")]
public class Pokemon : ScriptableObject
{
    [SerializeField]
    private PokemonType _type;
}

public enum PokemonType
{
    Grass,
    Water,
    Fire
}
```

6. Return to the Project folder in Unity, and create a Pokemon via the Create > ScriptableObjects > Pokemon menu.

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344036292761096222/image.png?ex=67bf72d7&is=67be2157&hm=63f20a6545631206ca5fdd16f2bed50cfc134f13b4e6e82bfd9f05f05ecf9d3c&=&format=webp&quality=lossless&width=725&height=105)

7. Name it 'CustomPokemonData'

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344036658844270684/image.png?ex=67bf732e&is=67be21ae&hm=edaf9ddb3b23211cfb4b177c9abc47b0183e60bda4a977b054cf13ae040136c6&=&format=webp&quality=lossless)

8. Move over to the Inspector and click the 'Type' dropdown. Here our custom types are displayed.

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344037041305944116/image.png?ex=67bf7389&is=67be2209&hm=cc890eda41bb3505ca66f475702e524f5669aa8b1d172aeec91190a91b98cd83&=&format=webp&quality=lossless)

9. Return to the Pokemon.cs file. We will add some extra information before creating more Pokemon. Add serialized fields for the Pokemon's Health, Attack, Special Attack, Defense, Special Defense, and Speed.

```csharp
[CreateAssetMenu(fileName = "Pokemon", menuName = "ScriptableObjects/Pokemon")]
public class Pokemon : ScriptableObject
{
    [SerializeField]
    private PokemonType _type;

    [SerializeField]
    private int _baseHealth;

    [SerializeField]
    private int _baseAttack;

    [SerializeField]
    private int _baseSpecialAttack;

    [SerializeField]
    private int _baseDefense;

    [SerializeField]
    private int _baseSpecialDefense;

    [SerializeField]
    private int _baseSpeed;
}
```

10. Lastly, add a serialized field for a sprite, name and Pokedex description and number.

```csharp
[CreateAssetMenu(fileName = "Pokemon", menuName = "ScriptableObjects/Pokemon")]
public class Pokemon : ScriptableObject
{
    [SerializeField]
    private PokemonType _type;

    [SerializeField]
    private int _baseHealth;

    [SerializeField]
    private int _baseAttack;

    [SerializeField]
    private int _baseSpecialAttack;

    [SerializeField]
    private int _baseDefense;

    [SerializeField]
    private int _baseSpecialDefense;

    [SerializeField]
    private int _baseSpeed;

    [SerializeField]
    private Sprite _sprite;

    [SerializeField]
    private string _name;

    [SerializeField, TextArea(5,20)]
    private string _pokedexDescription;

    [SerializeField]
    private int _pokedexNumber;
}
```

11. Save the file and return to Unity. Notice how our CustomPokemonData object has all of the extra fields.

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344038652501688391/image.png?ex=67bf7509&is=67be2389&hm=81d7af6b61b62f2e4c374c2437471ebcb4419cb1423f4a3c0945aa37ebae0940&=&format=webp&quality=lossless&width=265&height=325)

12. Fill out the fields with the information for your Pokemon.

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344039473129979924/image.png?ex=67bf75cd&is=67be244d&hm=3a003e9f5e3e3a67c8f47833f8f08533b4ea19cba75ae5d1f592cc0981b1aaf4&=&format=webp&quality=lossless&width=267&height=325)

13. Make a copy of CustomPokemonData, and fill it out with different information.

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344040114711429241/image.png?ex=67bf7666&is=67be24e6&hm=be5c7136bcd9908b90b6e87d5cb68532e9152b88a14eac28c50c742f51252426&=&format=webp&quality=lossless&width=275&height=324)

We now have two instances of our Pokemon class, each holding separate information that is stored in our game's project files. These can be used as "blueprints" for creating specific versions of those Pokemon during runtime.

## Bonus Tip
Using this [GitHub package](https://github.com/h-sigma/PvCustomizer), you can assign individual icons to ScriptableObjects! Just install the package through the package manager and add the `[PvIcon]` tag above the sprite you'd like to use.

![img.png](https://media.discordapp.net/attachments/675897969005953037/1344044184100667433/image.png?ex=67bf7a30&is=67be28b0&hm=7ba908310a503b0d208ae21b18cea8f3ac5de054efdf01663cebbb92242a9ea3&=&format=webp&quality=lossless)
![img.png](https://media.discordapp.net/attachments/675897969005953037/1344045372959625276/image.png?ex=67bf7b4c&is=67be29cc&hm=b2cb6194f65728e319b9b908883632885b000e26e94713390bf0f8580731745e&=&format=webp&quality=lossless)

[How to install a UPM package from git](https://docs.unity3d.com/Manual/upm-ui-giturl.html)

## Troubleshooting
- Ensure your class inherits from ScriptableObject and not MonoBehaviour
- Ensure the CreateAssetMenu tag contains both an itemName and a menuName
- Ensure your properties are serialized for them to display in the Inspector.

## Extra Resources
- [ScriptableObject reference](https://docs.unity3d.com/Manual/class-ScriptableObject.html)
- [SerializeField reference](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/SerializeField.html)
- [CreateAssetMenu reference](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/CreateAssetMenuAttribute.html)
