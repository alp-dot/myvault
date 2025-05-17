---
created: 2025-05-14
tags:
  - python
  - pytest
  - unittest
description: 
reference:
---
```python
# Define tests using the unittest framework.
# It must start with "test_".
def test_initialize_gemini_with_provided_key(self):
# Write what to test in the Docstrings.
        """Test initializing Gemini with a provided API key."""
        # Treat the specified method only between the with clause as mock_configure
        with patch("google.generativeai.configure") as mock_configure:

            initialize_gemini(TEST_API_KEY)
            # 
            mock_configure.assert_called_once_with(api_key=TEST_API_KEY)
```
