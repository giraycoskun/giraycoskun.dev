<!--- file: docs/howto/embedding_pdf.md --->
{% with pdf_file = "../../assets/artifacts/cv.pdf" %}

{% set solid_filepdf = '<i class="fas fa-file-pdf"></i>' %}
{% set empty_filepdf = '<i class="far fa-file-pdf"></i>' %}

<embed width=150% height=1000 src="{{ pdf_file }}" type="application/pdf" />

{% endwith %}