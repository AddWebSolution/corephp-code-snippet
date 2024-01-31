# Composer file
 - php unit installed as package
 - used psr-4 autoload with directory name **src**
```
{
    "require": {
        "phpunit/phpunit": "^8"
    },
    "autoload": {
        "psr-4": {
            "": "src/"
        }
    }
}

```

# Create a Article Slug with Namespace

```
<?php

namespace App;

class Article {

    public $title;

    public function getSlug()
    {
        $slug = $this->title;
        
        $slug = str_replace(' ', '_', $slug);
        
        return $slug;                        
    }
}
```

# Test Case Code 

```
<?php

use PHPUnit\Framework\TestCase;

class ArticleTest extends TestCase
{
    protected $article;
    
    protected function setUp(): void
    {
        $this->article = new App\Article;        
    }
    
    public function testTitleIsEmptyByDefault()
    {
        $this->assertEmpty($this->article->title);
    }
    
    public function testSlugIsEmptyWithNoTitle()
    {
        $this->assertSame($this->article->getSlug(), "");        
    }
    
    public function testSlugHasSpacesReplacedByUnderscores()
    {
        $this->article->title = "An example article";
        
        $this->assertEquals($this->article->getSlug(), "An_example_article");
    }    
}
```

# Php Unit Test Case
![image](https://github.com/AddWebSolution/corephp-code-snippet/assets/122769306/470bd629-3ccd-41f0-812c-277c821945c8)
