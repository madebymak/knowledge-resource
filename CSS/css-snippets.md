# CSS Snippets

## Modal Slide Up
```
.modal {
	transform: translateY(30px);
	visibility: hidden;
	opacity: 0;
	transition: all 0.35s;
}

.modal-open {
	transform: translateY(0);
	visibility: visible;
	opacity: 1;
}
```
