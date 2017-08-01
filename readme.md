# XML2JSON

> XML2JSON for ES2015 Module (Not CommonJS Module)


## Install

```
Not Upload to NPM right now, you can get xml2json by git clone
```

## Usage

```js
import xml2json from './kit/xml2json'; //Not push xml2json to NPM now,so you can use relative or absolute path

//parse your xml string here
function parseToJSON(xml){
    return xml2json.toJSON(xmlContent);
} 

//parse your json to XML Object here
function parseToXML(json){
    return xml2json.toXML(test2);
}

//parse your xml string to really XML Object
function getOriginXML(xmlString){
    return xml2json.getXmlObject(xmlContent)
}

//simulate ajax XML file and parse data
function ajaxData(){
    axios.get('./my.xml').then(success=>{
        //parse data
        var xmlContent = success.data
        var xmlObject = getOriginXML(xmlContent);
        var json = parseToJSON(xmlContent);
        var parsedXML = parseToXML(json);
    }).catch(error=>{
        //handle error
    })    
}
```

## JSON Format

if you invoke xml2json.toJSON(xmlstring), the return JSON Format Will be like this

```js
    {
        tagName: "Root TagName",
        hasAttr: true | false, //indicate whether there's attributes in current tag
        isParent: true | false, //indicate whether there's child tags in current tag        
        content: "this is content", //show current tag's content, it's contains arrow tag if it's not leaf node (just child node,without own children) 
        attr: { //show current tag's attributes set, it's just like <Example attr1="attr1's val" attr2="attr2's val"></Example>, if there's no attr, the attr attrbutes will be a empty object;
            attr1: "attr1's val",
            attr2: "attr2's val"
        },
        children: [ //it's same struture.if some child without own children, it's will don't own children key, and the isParent will be set to false
            {
                ...
            }
        ]
    }

```


## Infomation

The xml2json plugin is used in es2015 module, write with es2015 syntax, may not suit for CommonJS module. 

If it can help to you, please give me a star, Thanks a lot! :P

## License

MIT
