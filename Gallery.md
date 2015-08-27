---
layout: default
title: Gallery
permalink: /gallery/
gallery: true
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
<div class="row">
    {% for photo in site.data.photos %}
    <div class="col-sm-4 col-md-3">
        <div class="thumbnail {% cycle 'thb-success','thb-info','thb-warning','thb-danger' %}">
            <img src="{{ photo.src }}" alt="...">
            <div class="caption">
                <h3 class="photo-label">{{ photo.label }}</h3>
                <p>
                    {{ photo.caption }}
                </p>
                <p>
                    Photo by: {{ photo.credit }}
                </p>
                <p>
                    <a href="{{ photo.src  | replace:'2', '7'}}" class="btn btn-primary" role="button">View Original</a>
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
                            <img class="thumbnail img-responsive center-block" src="{{ photo.src  | replace:'2', forloop.index}}" alt="{{ photo.label }}">
                            <div class="carousel-caption">
                                {{ photo.caption }}
                                <a href="{{ photo.src  | replace:'2', forloop.index}}"> View Original</a>
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