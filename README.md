# nuklear_cairo
Frame buffer backend for Nuklear using Cairo software rendering.

```c
int main(...) {
	// run once
	nk_cairo_init();
  
	// multiple fonts are fine
	struct nk_user_font *font = nk_cairo_ttf("path/to/font.ttf", 24);

	struct nk_context ctx;
	nk_init_default(&ctx, font);

	int width = 1000;
	int height = 1000;
	int pitch = width * sizeof(uint32_t);
	void *frame = malloc(height * pitch);

	nk_begin(&ctx, nk_rect(0, 0, width, height), ...);
		// usual Nuklear stuff
	nk_end(&ctx);

	nk_cairo_render(&ctx, frame, width, height, pitch);
	// now do what you like with frame
}
```
