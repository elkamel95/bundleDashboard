# bundleServeurDashboard
1. install : composer require generic/dashboard
2. create controller end extends widgteControler
3. Create an end of widget entity copy this code into this entity

```
<?php

namespace App\Entity;

use ApiPlatform\Core\Annotation\ApiResource;
use Doctrine\ORM\Mapping as ORM;
use ApiPlatform\Core\Annotation\ApiFilter;
use ApiPlatform\Core\Bridge\Doctrine\Orm\Filter\SearchFilter;
use ApiPlatform\Core\Bridge\Doctrine\Orm\Filter\OrderFilter;
use ApiPlatform\Core\Bridge\Doctrine\Orm\Filter\DateFilter;
use ApiPlatform\Core\Bridge\Doctrine\Orm\Filter\BooleanFilter;

/**
 * @ApiResource()
  * @ApiFilter(DateFilter::class, properties={"create_at","updateAt"})
 * @ApiFilter(SearchFilter::class, properties={"id": "exact", "name_fr": "partial",
 *  "name_fr": "word_start" ,"name_en":"word_start","type":"exact","users.id":"exact"})
 * @ApiFilter(OrderFilter::class, properties={"updateAt","create_at","type"})
 * @ApiFilter(BooleanFilter::class, properties={"visible"})

 * @ORM\Entity(repositoryClass="App\Repository\WidgetRepository")
 * @ORM\HasLifecycleCallbacks
 */

class Widget
{
    /**
     * @ORM\Id()
     * @ORM\GeneratedValue()
     * @ORM\Column(type="integer")
     */
 
    private $id;

    /**
     * @ORM\Column(type="string", length=255)
     */
    private $name_fr;

    /**
     * @ORM\Column(type="string", length=255)
     */
    private $name_en;

    /**
     * @ORM\Column(type="string", length=255)
     */
    private $description;

    /**
     * @ORM\Column(type="string", length=255 ,nullable=true)
     */
    private $url;

    /**
     * @ORM\Column(type="string", length=255 ,nullable=true)
     */
    private $text_color;

    /**
     * @ORM\Column(type="string", length=255 ,nullable=true)
     */
    private $background_color;

  

    /**
     * @ORM\Column(type="string", length=255 ,nullable=true)
     */
    private $font;

    /**
     * @ORM\Column(type="string" ,nullable=true,options={"default" : ""})
     */
    private $position_left;

    /**
     * @ORM\Column(type="string" ,nullable=true)
     */
    private $position_right;

    /**
     * @ORM\Column(type="string", length=255 )
     */
    private $type;

    /**
     * @ORM\Column(type="string", nullable=true)
     */
    private $create_at;

    /**
     * @ORM\Column(type="boolean", nullable=true ,options={"default" : 1})
     */
    private $visible;

    /**
     * @ORM\Column(type="string", length=255, nullable=true)
     */
    private $updateAt;

    /**
     * @ORM\Column(type="float", length=255 ,nullable=true)
     */
    private $width;

    /**
     * @ORM\Column(type="float", length=255,nullable=true)
     */
    private $height;

    /**
     * @ORM\Column(type="string", length=255,nullable=true)
     */
    private $backgroundSmallWidget;

    /**
     * @ORM\Column(type="string", length=255,nullable=true)
     */
    private $colorSmallWidget;

    /**
     * @ORM\Column(type="string", length=255,nullable=true)
     */
    private $size;

    /**
     * @ORM\ManyToOne(targetEntity="App\Entity\User", inversedBy="widgets")
     */
    private $users;

    public function getId(): ?int
    {
        return $this->id;
    }

    public function getNameFr(): ?string
    {
        return $this->name_fr;
    }

    public function setNameFr(string $name_fr): self
    {
        $this->name_fr = $name_fr;

        return $this;
    }

    public function getNameEn(): ?string
    {
        return $this->name_en;
    }

    public function setNameEn(string $name_en): self
    {
        $this->name_en = $name_en;

        return $this;
    }

    public function getDescription(): ?string
    {
        return $this->description;
    }

    public function setDescription(string $description): self
    {
        $this->description = $description;

        return $this;
    }

    public function getUrl(): ?string
    {
        return $this->url;
    }

    public function setUrl(string $url): self
    {
        $this->url = $url;

        return $this;
    }

    public function getTextColor(): ?string
    {
        return $this->text_color;
    }

    public function setTextColor(string $text_color): self
    {
        $this->text_color = $text_color;

        return $this;
    }

    public function getBackgroundColor(): ?string
    {
        return $this->background_color;
    }

    public function setBackgroundColor(string $background_color): self
    {
        $this->background_color = $background_color;

        return $this;
    }



    public function getFont(): ?string
    {
        return $this->font;
    }

    public function setFont(string $font): self
    {
        $this->font = $font;

        return $this;
    }

    public function getPositionLeft(): ?string
    {
        return $this->position_left;
    }

    public function setPositionLeft(string $position_left): self
    {
        $this->position_left = $position_left;

        return $this;
    }

    public function getPositionRight(): ?string
    {
        return $this->position_right;
    }

    public function setPositionRight(string $position_right): self
    {
        $this->position_right = $position_right;

        return $this;
    }

    public function getType(): ?string
    {
        return $this->type;
    }

    public function setType(string $type): self
    {
        $this->type = $type;

        return $this;
    }

    public function getCreateAt(): ?string
    {
        return $this->create_at;
    }

    public function setCreateAt(string $create_at): self
    {
        $this->create_at = $create_at;

        return $this;
    }

    public function getVisible(): ?bool
    {
        return $this->visible;
    }

    public function setVisible(?bool $visible): self
    {
        $this->visible = $visible;

        return $this;
    }

    public function getUpdateAt(): ?string
    {
        return $this->updateAt;
    }

    public function setUpdateAt(?string $updateAt): self
    {
        $this->updateAt = $updateAt;

        return $this;
    }

    public function getWidth(): ?float
    {
        return $this->width;
    }

    public function setWidth(float $width): self
    {
        $this->width = $width;

        return $this;
    }

    public function getHeight(): ?float
    {
        return $this->height;
    }

    public function setHeight(float $height): self
    {
        $this->height = $height;

        return $this;
    }

    public function getBackgroundSmallWidget(): ?string
    {
        return $this->backgroundSmallWidget;
    }

    public function setBackgroundSmallWidget(string $backgroundSmallWidget): self
    {
        $this->backgroundSmallWidget = $backgroundSmallWidget;

        return $this;
    }

    public function getColorSmallWidget(): ?string
    {
        return $this->colorSmallWidget;
    }

    public function setColorSmallWidget(string $colorSmallWidget): self
    {
        $this->colorSmallWidget = $colorSmallWidget;

        return $this;
    }

    public function getSize(): ?string
    {
        return $this->size;
    }

    public function setSize(string $size): self
    {
        $this->size = $size;

        return $this;
    }

     /**
     * @ORM\PrePersist()
      */
  public function setDefaultValues() {
$this->setPositionRight('');
$this->setPositionLeft('');

}

  public function getUsers(): ?User
  {
      return $this->users;
  }

  public function setUsers(?User $users): self
  {
      $this->users = $users;

      return $this;
  }
}
````
4. copy this code into "api_platform.yaml"
````
api_platform:
    mapping:
        paths: ['%kernel.project_dir%/src/Entity']
     # Default value
    collection:
            pagination:
                items_per_page_parameter_name: itemsPerPage # Default value
                client_items_per_page: true # Disabled by default
                enabled: true
                page_parameter_name: page
                client_enabled: true
    swagger:
         api_keys:
             apiKey:
                name: Authorization
                type: header


    # The list of enabled error formats. The first one will be the default.
   

````
5. create an xml file with the name configEntity and copy this code into this file
````
<entities>
 <entity  identifier ="" name= "" enterpoint = "" value="">

    <attribute name ="" header=""  value="" type=""> </attribute>
<! -- Si l’objet de type Array et liste est statique nous définissons la liste
Statiquement comme ça 
    <attribute name ="" value="" type="">

     <property name=""  value="" ></property >
      <property name="" value=""></property >
      ......
    </attribute>
 -->

<! -- Si l’objet de type Array et liste est dynamique nous définissons la liste
comme ça : 
   <attribute name ="" enterpoint = ""    value="" type="">
      <property name=""  value="" ></property >
   </attribute>
 -->


   <attribute name = "" value="" type="" session_value="" session_name="">
</attribute>

  </entity>

````
6. php bin/console doctrine:schema:update --force
7. run serve 

