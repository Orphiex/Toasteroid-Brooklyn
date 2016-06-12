<div class="hero{% if hero_full_height %} hero--full-height{% endif %}{% if hero_first_on_page %} hero--first{% endif %}" id="Hero"{% if hero_full_height %} data-fullscreen="true"{% endif %}{% if hero_parallax %}data-parallax="true"{% endif %}>
  {% for i in (1..6) %}
    {% capture slide %}hero_slide_{{ i }}_enable{% endcapture %}
    {% capture slide_img %}hero_slide_{{ i }}.jpg{% endcapture %}
    {% capture slide_text_color %}hero_slide_{{ i }}_text_color{% endcapture %}
    {% capture slide_heading %}hero_slide_{{ i }}_heading{% endcapture %}
    {% capture slide_subheading %}hero_slide_{{ i }}_subheading{% endcapture %}
    {% capture slide_picture %}hero_slide_{{ i }}_picture{% endcapture %}
    {% capture slide_cta %}hero_slide_{{ i }}_cta{% endcapture %}
    {% capture slide_link %}hero_slide_{{ i }}_link{% endcapture %}
    {% if settings[slide] %}
      <div class="hero__slide {{ settings[slide_text_color] }}" data-color="{{ settings[slide_text_color] }}">
        {% if hero_full_height %}
          {% comment %}
            Full-screen styles use CSS background images
          {% endcomment %}

          <style>
            @media screen and (max-width: 1024px) and (max-height: 768px)  {
              .hero__image--{{ i }} {
                background-image: url('{{ slide_img | asset_img_url: '1024x1024' }}');
              }
            }
            @media screen and (min-width: 1025px), screen and (min-height: 769px) {
              .hero__image--{{ i }} {
                background-image: url('{{ slide_img | asset_img_url: '2048x2048' }}');
              }
            }
          </style>

          <div class="hero__image hero__image--{{ i }}" data-image="{{ slide_img | asset_url }}"></div>
        {% else %}
          <div class="hero__image">
            <img src="{{ slide_img | asset_img_url: '2048x2048' }}" alt="{{ settings[slide_heading] }}">
          </div>
        {% endif %}
        <div class="hero__text-wrap">
          <div class="hero__text-align">
            <div class="hero__text-content">
              {% unless settings[slide_heading] == blank %}
                <h1 class="hero__title">
                  {{ settings[slide_heading] }}
                </h1>
              {% endunless %}
              {% unless settings[slide_subheading] == blank %}
                <p class="hero__subtitle">
                  {{ settings[slide_subheading] }}
                </p>
              {% endunless %}
              {% unless settings[slide_cta] == blank %}
                <a href="{{ settings[slide_link] }}" class="btn hero__cta">
                  {{ settings[slide_cta] }} <span class="icon icon-arrow-right" aria-hidden="true"></span>
                </a>
              {% endunless %}
              {% unless settings[slide_picture] == blank %}
                <img class="hero_slide-picture" src="{{ settings[slide_picture] }}" alt="">
              {% endunless %}
            </div>
          </div>
        </div>
        <!-- <div class="hero__picture-wrap">
          <div class="hero__picture-align">
            
          </div>
        </div> -->
      </div>
    {% endif %}
  {% endfor %}
</div>