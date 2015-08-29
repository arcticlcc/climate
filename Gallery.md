---
layout: default
title: Gallery
permalink: /gallery/
gallery: true
fullbase: http://data.arcticlcc.org/climate/
---

<div class="jumbotron">
    <h2><span class="glyphicon glyphicon-camera" aria-hidden="true"></span> Photo Gallery </h2>
    <p>
        This gallery contains images of climate change effects on Alaska's
        ecosystems and associated cultural resources. Each image has a caption,
        source, and link to a high resolution version. Click the thumbnails to
        preview. While use of these images is not restricted, we ask that you
        credit the source when using them.
    </p>
</div>

<div class="gallery row">
    {% for photo in site.data.photos %}
    {% assign mod = forloop.index | modulo:4 %}
        <div class="col-sm-4 col-md-3">
            <div class="thumbnail {% cycle 'thb-success','thb-info','thb-warning','thb-danger' %}">
                <img src="{{ site.baseurl }}/images/gallery/250/arctic_climate_{{ photo.src }}_250.jpg" alt="{{ photo.title }}" title="{{ photo.title }}" />
                <div class="caption">
                    <h3 class="photo-label">{{ photo.label }}</h3>
                    <p>
                        {{ photo.caption }}
                    </p>
                    <p class="photo-credit">
                        <small>Photo by: <a href="{{ photo.origin_src }}">{{ photo.credit }}</a></small>
                    </p>
                    <p>
                        <a href="{{ page.fullbase }}arctic_climate_{{ photo.src }}.jpg" class="btn btn-primary" role="button">View Original</a>
                    </p>
                </div>
            </div>
        </div>
    {% endfor %}
</div>

<!-- Modal -->
<div class="modal fade" id="galleryModal" tabindex="-1" role="dialog" aria-labelledby="galleryModalLabel">
    <div class="modal-dialog modal-lg" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
                <h4 class="modal-title" id="galleryModalLabel">Modal title</h4>
            </div>
            <div class="modal-body">
                <div id="carousel-gallery" class="carousel slide" data-ride="carousel" data-interval="false">
                    <!-- Wrapper for slides -->
                    <div class="carousel-inner" role="listbox">
                        {% for photo in site.data.photos %}
                        <div class="item {% if forloop.first %}active{% endif %}">
                            <img class="thumbnail img-responsive center-block" src="{{ site.baseurl }}/images/gallery/1024/arctic_climate_{{ photo.src }}_1024.jpg" alt="{{ photo.title }}" title="{{ photo.title }}">
                            <div class="carousel-caption hidden-xs">
                                {{ photo.caption }}
                                <br/>
                                <a href="{{ page.fullbase }}arctic_climate_{{ photo.src }}.jpg">
                                View Original</a>
                            </div>
                        </div>
                        {% endfor %}
                    </div>
                    <!-- Controls -->
                    <a class="left carousel-control" href="#carousel-gallery" role="button" data-slide="prev"> <span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span> <span class="sr-only">Previous</span> </a>
                    <a class="right carousel-control" href="#carousel-gallery" role="button" data-slide="next"> <span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span> <span class="sr-only">Next</span> </a>
                </div>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-success" data-dismiss="modal">
                    Close
                </button>
            </div>
        </div>
    </div>
</div>