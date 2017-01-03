[![Build Status](https://travis-ci.org/dwolfhub/zxcvbn-python.svg?branch=master)](https://travis-ci.org/dwolfhub/zxcvbn-python)

# zxcvbn-python
Python implementation of Dropbox's realistic password strength estimator. The original library, written for JavaScript, can be found [here](https://github.com/dropbox/zxcvbn).

While there may be other Python ports available, this one is the most up to date and is reccommended by the original developers of zxcvbn at this time.

Tested in Python versions 2.6-2.7, 3.3-3.5

## Installation

Install the package using pip: `pip install zxcvbn-python`

## Usage

Pass a password as the first parameter, and a list of user-provided inputs as the `user_inputs` parameter (optional).

```python
from zxcvbn import zxcvbn

results = zxcvbn('JohnSmith123', user_inputs=['John', 'Smith'])

print(results)
```

Output:

```
{
    'password': 'JohnSmith123', 
    'score': 2, 
    'guesses': 2567800, 
    'guesses_log10': 6.409561194521849, 
    'calc_time': datetime.timedelta(0, 0, 5204)
    'feedback': {
        'warning': '', 
        'suggestions': [
            'Add another word or two. Uncommon words are better.', 
            "Capitalization doesn't help very much"
        ]
    }, 
    'crack_times_display': {
        'offline_fast_hashing_1e10_per_second': 'less than a second'
        'offline_slow_hashing_1e4_per_second': '4 minutes', 
        'online_no_throttling_10_per_second': '3 days', 
        'online_throttling_100_per_hour': '3 years', 
    }, 
    'crack_times_seconds': {
        'offline_fast_hashing_1e10_per_second': 0.00025678, 
        'offline_slow_hashing_1e4_per_second': 256.78
        'online_no_throttling_10_per_second': 256780.0, 
        'online_throttling_100_per_hour': 92440800.0, 
    }, 
    'sequence': [{
        'matched_word': 'john', 
        'rank': 2, 
        'pattern': 'dictionary', 
        'reversed': False, 
        'token': 'John', 
        'l33t': False, 
        'uppercase_variations': 2, 
        'i': 0, 
        'guesses': 50, 
        'l33t_variations': 1, 
        'dictionary_name': 'male_names', 
        'base_guesses': 2, 
        'guesses_log10': 1.6989700043360185, 
        'j': 3
    }, {
        'matched_word': 'smith123', 
        'rank': 12789, 
        'pattern': 'dictionary', 
        'reversed': False, 
        'token': 'Smith123', 
        'l33t': False, 
        'uppercase_variations': 2, 
        'i': 4, 
        'guesses': 25578, 
        'l33t_variations': 1, 
        'dictionary_name': 'passwords', 
        'base_guesses': 12789, 
        'guesses_log10': 4.407866583030775, 
        'j': 11
    }], 
}
```